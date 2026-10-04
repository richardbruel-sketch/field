# Format de flux Field (version 1)

Un match en direct peut avoir un flux : dans `matchs.json`, ajouter `"flux": "adresse.json"` à l'entrée du match.
L'appli relit cette adresse toutes les 3 secondes. Le fichier est un instantané de l'état du match. Si le flux répond, la mention passe à « Flux en direct » ; sinon « Flux indisponible ». Sans flux, l'animation reste en démonstration (« Données simulées »).

Repères : `x` et `y` vont de 0 à 1, origine en haut à gauche de la scène. Pour le football, l'équipe `a` attaque vers la droite.

## Champs communs
`version` (1), `sport`, `minute` (facultatif), `score` (facultatif), `evenement` (texte court).

## Football
`joueurs`: liste de `{eq:"a"|"b", num, x, y}` · `balle`: `{x,y}` · `acteur`: `{eq,num}` (joueur en action).

## Voile (SailGP)
`bateaux`: liste de `{nation:"FRA", x, y, vitesse (km/h), rang}`. Drapeaux fournis : FRA, GBR, AUS, USA, NZL (les autres affichent le code).

## Golf
`joueurs`: `{code, nom, score}` · `en_cours`: code du joueur qui joue · `coups`: dernière position de chaque balle, `{j: code, x, y}`.

## Tennis
`joueurs`: `[{code,nom},{code,nom}]` · `service`: 0 ou 1 · `en_action`: 0 ou 1 · `score` (texte) · `balle`: `{x,y}` · `positions`: `[{x,y},{x,y}]`.

## Formule 1
`tour` · `voitures`: `{code (3 lettres), p (position sur le circuit, 1,25 = un quart du tour 2), rang, ecart (secondes), couleur (facultatif)}`.

## À savoir
- Les fichiers du dossier `feeds/` sont des exemples. Pour les essayer : renommer `matchs-test.json` en `matchs.json`.
- Les données doivent venir d'un fournisseur sous licence commerciale (voir le PDF des limites légales).
- Ne mets pas de clé d'API dans l'appli : elle serait visible de tous. Si le fournisseur impose une clé, un petit serveur qui transmet uniquement ces données (jamais du son ni de l'image) peut la garder secrète.
- Le flux doit autoriser les requêtes depuis ton site (CORS).
