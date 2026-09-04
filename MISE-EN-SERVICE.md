# Relevé de stock — mise en service

## Ce que fait l'application

- Scan des codes-barres articles avec la caméra du téléphone (EAN-13/8, Code 128, Code 39, ITF, UPC, QR, DataMatrix)
- Recherche automatique de la désignation dans une base articles importée depuis Excel
- Saisie de la quantité disponible, article par article
- **Cumul automatique** : un article scanné deux fois additionne les quantités (bouton « Remplacer » disponible si besoin)
- Correction et suppression des lignes dans l'onglet Relevé
- Envoi du relevé par WhatsApp, e-mail, fichier CSV ou copie de texte
- Fonctionne hors ligne une fois installée ; les données sont conservées si l'application est fermée

## Hébergement (obligatoire)

La caméra n'est accessible qu'en **HTTPS**. Un fichier ouvert directement depuis le téléphone (`file://`) ne fonctionnera pas.

**Option la plus simple — GitHub Pages, gratuit :**

1. Créer un compte sur github.com, puis un dépôt public nommé par exemple `releve-stock`
2. Téléverser les 3 fichiers : `releve-stock.html`, `manifest.json`, `sw.js`
3. Settings → Pages → Source : « Deploy from a branch » → branche `main`, dossier `/root` → Save
4. Au bout de 1 à 2 minutes l'adresse est disponible :
   `https://VOTRE-COMPTE.github.io/releve-stock/releve-stock.html`

Autres options équivalentes : Netlify Drop (glisser-déposer du dossier), Cloudflare Pages, ou un sous-dossier de votre site existant.

## Installation sur les téléphones

1. Ouvrir l'adresse dans **Chrome** sur Android
2. Menu ⋮ → « Ajouter à l'écran d'accueil »
3. Lancer depuis l'icône : l'application s'ouvre en plein écran, sans barre de navigateur
4. Au premier scan, autoriser l'accès à la caméra

## Base articles

Format attendu, une ligne par article :

```
Code;Désignation;Unité
3760012345678;Salvia nemorosa Caradonna P9;plaque de 24
```

- La 3ᵉ colonne est facultative
- Depuis Excel : Fichier → Enregistrer sous → **CSV (séparateur : point-virgule)**
- Import dans l'onglet Réglages → « Importer un fichier CSV »
- La base reste en mémoire sur le téléphone ; à réimporter uniquement en cas de mise à jour du catalogue

Un article scanné hors base reste enregistrable : il apparaît en orange, avec son seul code. Utile pour repérer les codes manquants au catalogue.

## Réglages à faire une fois par téléphone

Onglet Réglages : nom du site, nom de l'opérateur, adresse e-mail et numéro WhatsApp de destination (format international sans `+`, par exemple `33612345678`).

## Points d'attention

- **WhatsApp** : le message passe par une URL ; au-delà d'environ 100 lignes, préférer le CSV
- **E-mail** : `mailto:` ne peut pas joindre de fichier. Pour un envoi avec pièce jointe, utiliser « Fichier CSV » puis joindre le fichier depuis l'application mail
- **Sauvegarde** : le relevé est stocké dans le navigateur du téléphone. Ne pas effacer les données de navigation avant d'avoir envoyé le relevé
- **Éclairage** : le bouton ☀ en haut à droite active la lampe si le téléphone le permet

## Évolutions possibles

- Envoi direct vers une boîte mail ou un Google Sheet sans manipulation de l'opérateur (nécessite un petit script côté serveur)
- Consolidation automatique des relevés de plusieurs sites dans un classeur Excel unique
- Empaquetage en fichier APK installable, si vous souhaitez éviter le passage par Chrome
