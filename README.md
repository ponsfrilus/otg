# OTP - One Time Password

OTP est un projet pour l'EPFL dont le but est de pouvoir transmettre des secrets (par exemple un mot de passe) à une tierce personne de manière sécurisée et éviter les [agressions plein texte](http://plaintextoffenders.com/) (plain text offenders).

## Principe de base
La personne A crée le secret sur le site et récupère le lien pour le transmettre à la personne B. Lorsque la personne B suit le lien, elle peut alors voir le secret et un message indiquant qu'il a maintenant été révoqué. Le lien utilisé, il n'est plus possible de connaître le secret.

## Cas d'utilisation 1
Lors de l'accueil d'une nouvelle personnes à l'EPFL, un collaborateur ayant les privilèges suffisant doit initialiser le compte de la personne (en résumé lui assigner un mot de passe). Dans les cas ou la personne n'est pas physiquement présente pour saisir elle-même le dit mot de passe, le collaborateur doit alors communiquer ce mot de passe à la personne.

## Première version
La première version du site doit permettre les fonctionnalités suivantes:
  1. Création du secret
     * Champ pour saisir le secret
     * Champ pour saisir le destinataire du secret
     * Champ pour saisir un message au destinataire du secret
  1. Création de la page d'affichage du secret, avec
      * Un avertissement sur la révocation du secret
    * Le message que le créateur du secret à destiné au récepteur
     * Le secret lui-même
  1. L'envoi du secret par email, avec
     * L'avertissement sur la révocation du secret
     * Le lien vers le secret
     * Le message du créateur du secret

Note que le système doit être capable de stocker les secrets de manière 100% sécure et que seule la clé contenue dans le lien doit être capable de le décrypter.

## Seconde version
La seconde version du site n'autoriser que les personnes accréditées à utiliser le système (i.e. Tequila) et doit, selon le même principe que la première version, assurer l'identité de la personne qui doit recevoir le secret.

## Troisième version
La troisième version du système de doit pas limiter les secrets à un champ texte, mais doit accepter des documents (images, pdf, etc...) sous le même principe.

## Autres améliorations possibles (en vrac)
  * Proposer un générateur de mot de passe sécure, humainement lisible (aka prononçable), etc...
  * [HOTP](https://tools.ietf.org/html/rfc4226) - Permettre le choix du nombre d'utilisation du lien (nombre d'affichage du secret) (HOTP: An HMAC-Based One-Time Password Algorithm)
  * [TOTP](https://tools.ietf.org/html/rfc6238) - Permettre de mettre une date d'expiration au secret (TOTP: Time-Based One-Time Password Algorithm)
  * Permettre de choisir le mode du secret (entre nombre d'affichage ou date d'expiration ou les deux)
  * S'assurer de la destruction du secret (lifetime) s'il n'a pas été vu/lu d'ici à dans x jours
  * Notifier le créateur du secret de l'utilisation de son lien
  * Prévoir le multilinguisme de l'application (FR + EN + ???)
  * Ne pas forcément utiliser le mail pour partager le lien, prévoir le partage sur d'autres systèmes de messagerie (e.g. what's app, Telegram, Signal, etc...)
  * Créer un API avec des clés liées à des comptes sciper pour créer des secrets en ligne de commandes
  * Créer un bot Telegram pour créer des secrets et les partager directement depuis Telegram

# Systèmes similaires (en vrac)
  * https://onetimesecret.com/
  * http://whisperpassword.com/
  * https://www.thismessagewillselfdestruct.com/
  * https://github.com/Achiel/SecretSexChange
  * http://sebsauvage.net/paste/
  * https://pwpush.com/
  * http://searchsecurity.techtarget.com/definition/one-time-password-OTP
  * https://github.com/guyht/notp
  * https://github.com/markbao/speakeasy
