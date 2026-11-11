# Site de documentation de Marée

Deux pages statiques, sans dépendance et sans JavaScript : uniquement les
deux URL qu'App Store Connect réclame, rien d'autre.

| Fichier | Sert à |
|---|---|
| `confidentialite.html` | **Privacy Policy URL** d'App Store Connect |
| `support.html` | **Support URL** d'App Store Connect |
| `style.css` | Jetons de design repris de l'app |
| `fonts/` | Fredoka et Nunito, auto-hébergées, avec leurs licences OFL |

Il n'y a **pas de page d'accueil** : la racine du site renvoie un 404, ce qui
est sans conséquence puisque Apple ne demande que les deux adresses
ci-dessous. Les deux pages se renvoient l'une à l'autre.

## Valeurs en place

| Donnée | Valeur |
|---|---|
| Éditeur / responsable de traitement | Proion Conseil |
| Adresse de support | contact@proion.fr |

Pour les changer, passe partout d'un coup :

```bash
sed -i '' 's/contact@proion\.fr/nouvelle@adresse.fr/g' confidentialite.html support.html
```

Et pense à remonter la date en haut de `confidentialite.html` si le fond
change.

## Publier sur GitHub Pages

1. Copie le contenu de ce dossier à la racine du dépôt de documentation, ou
   dans un sous-dossier `docs/`.
2. Sur GitHub : **Settings → Pages**, source **Deploy from a branch**, branche
   `main`, dossier `/ (root)` ou `/docs` selon ce que tu as choisi.
3. Attends la fin du déploiement, puis **ouvre les deux URL dans une fenêtre
   de navigation privée**. C'est le test qui compte : si elles s'affichent
   sans être connecté, un reviewer d'Apple les verra aussi.

Les deux URL en ligne :

```
https://proionapplib.github.io/maree/confidentialite.html
https://proionapplib.github.io/maree/support.html
```

Ce sont ces deux adresses à coller dans App Store Connect, dans
**App Information** (politique de confidentialité) et dans la version de l'app
(URL de support).

## Pourquoi les polices sont dans le dépôt

Une page qui promet de ne rien collecter ne doit pas appeler Google Fonts :
l'IP du visiteur partirait chez un tiers, ce qui a déjà valu des
condamnations en Europe. Fredoka et Nunito sont donc servies depuis `fonts/`.
Leur licence SIL OFL autorise cette redistribution, à condition de conserver
les fichiers de licence — c'est pour ça qu'ils sont là, ne les supprime pas.

Résultat : les pages ne font **aucune requête vers un domaine tiers**.

## Cohérence avec la fiche App Store

La politique affirme que rien n'est collecté. Il faut donc déclarer
**« Aucune donnée collectée »** dans les étiquettes de confidentialité d'App
Store Connect. C'est la cohérence entre les deux que la revue vérifie.

## Ce qui n'est pas couvert

Ces pages sont écrites pour décrire fidèlement ce que fait l'app, pas pour
tenir lieu de conseil juridique. Si tu édites sous une structure commerciale,
fais-les relire — en particulier la mention du responsable de traitement et
la base légale.
