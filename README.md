# Tiw-Moteur-de-recherche-
## Moteur de recherche :CSS, HTML, PHP,MySql / indexation de document
## I. Module d'indexation de document :
''''''''''''''''''''''''''''''''''''

### indexer n’importe quel texte brute :
------------------------------------

1- mise en minuscule pour rendre la forme des mots homogène

2- opération de tokenisation : on découpe le texte sur la base d'un ensemble de caractères de séparation !  l'espace + tous les caractères de ponctuation + les caractères de type [{( etc.

3- 1er filtrage au moment du découpage par taille, on supprime tout ce qui est <=2  et on utilise aussi un dictionnaire de mots vides (articles, adverbes, syntagmes, etc.)

4- on filtre et on calcule encore une fois, les occurrences des mots, cela supprime les doublons et donne aussi des statistiques précises sur la présence des mots dans le texte

5- mise en base de données :enregistrement des résultats des l'indexation

La base de données doit refléter les besoins de l'indexation, document->mot-poids,  cela se traduit par un besoin de représenter ces trois entités, donc document, mot et document-mot (le lien entre les deux avec le poids). La table des mots ne doit pas contenir de doublons, la table document ne doit pas aussi contenir deux fois un même document !

- affichage et présentation des traces du module indexation :
-------------------------------------------------------------
A l'exécution du module, le script doit présenter le déroulement de l’indexation par des statistiques pour chaque document indexé et NON par une suite de listes de mots longues et difficile à comprendre et à suivre. Les statistiques résumeraient mieux les résultats pour chaque document et du coup pour l’ensemble des textes à indexer.


## II. Module de recherche et visualisation:
'''''''''''''''''''''''''''''''''''''''''

1- rechercher par mots-clés : interface avec simple champ de recherche
-----------------------------
Cette interface se présente comme celle de google, simple mais efficace car elle cache le gros du travail derrière !  Elle doit chercher dans la base de données :

-si un mot est trouvé alors on trouve le document et les occurrences
-le classement se fera uniquement par les occurrences du mot dans les documents trouvés
-chaque résultat se présente comme sur google, le nom du document (en évidence) sous forme de lien pour accéder et  consulter le document, le résumé (100 à 150 caractères premiers caractères du texte !)
-les occurrences s'affichent entre parenthèse juste après le nom du document par exemple (un indicateur de pertinence)
-une lien viendra s'ajouter (nuage+) pour afficher sous le résumé,  en cliquant dessus le nuage s'affiche et sur (nuage-) le nuage disparaît, il ne doit pas s'afficher en permanence !
-le nuage des mots-clés est spécifique à chaque document et les mots-clés doivent appartenir à la liste des mots du document obtenus lors de l'indexation de celui-ci
-la taille de l'espace d'affichage du nuage est fixe pour tous les documents ! Le nombre de mots-clés par nuage est à modérer pour ne pas trop le charger, un nombre maximal est à définir, certains mots de poids 1  ou voire 2 peuvent ne pas être utilisés pour arriver à ce nombre maximal !

2- correcteur d'orthographe et d'erreurs de frappe :
----------------------------------------------------
vous devez réfléchir sur un algorithme qui vérifie la bonne orthographe d'une saisir de mot dans le champ de recherche avant toute affichage de résultats, c'est-à-dire, au moment de rechercher dans la table des mots !
cette fonction doit se faire à la fin après tout ce qui est demandé un peu plus haut
