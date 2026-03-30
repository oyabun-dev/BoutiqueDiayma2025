# Boutique Diayma

Etudiant : Khalifa Ababacar BEYE

## 2. Projets de la solution

La solution Diayma.sln contient un seul projet : P2FixAnAppDotNetCode (Diayma).

## 3. Version SDK .NET

Le projet utilisait à la base netcoreapp2.0 (.NET Core 2.0). J'ai dû migrer vers net10.0 car .NET Core 2.0 n'est plus supporté sur ma machine.

## 4. Installation du SDK

J'ai téléchargé et installé le SDK .NET 10 depuis https://dotnet.microsoft.com/download.

## 5. Dépôt GitHub

Lien du dépôt : https://github.com/oyabun-dev/BoutiqueDiayma2025

## 6. Bugs trouvés

Bug 1 : Le total des produits n'est pas bien calculé lorsqu'un produit est choisi 2 fois

Bug 2 : Le calcul de la moyenne est incorrecte car elle n'inclut pas les quantités

## 7. Points d'arrêt

J'ai placé des points d'arrêt sur les lignes suivantes :
- CartSummaryViewComponent.cs ligne 12
- ProductController.cs ligne 15
- OrderController.cs ligne 17
- CartController.cs ligne 15
- Startup.cs ligne 20

## 8. Namespaces, classes et méthodes visités avant l'affichage des produits

Quand on lance l'application et qu'on ouvre la page d'accueil, voici ce qui se passe dans l'ordre :

Le premier point d'arrêt atteint est Startup.cs ligne 20, dans la méthode ConfigureServices du namespace P2FixAnAppDotNetCode, classe Startup. C'est ici que les services sont enregistrés (MVC, localisation, repositories). J'ai utilisé le mode "Pas à pas principal" pour rester au niveau de Startup sans rentrer dans le détail des bibliothèques.

Ensuite, la méthode Configure de la même classe est exécutée pour configurer le pipeline HTTP.

Quand la requête GET arrive sur la page d'accueil, le point d'arrêt de ProductController.cs ligne 15 est atteint. C'est le constructeur de la classe ProductController dans le namespace P2FixAnAppDotNetCode.Controllers. J'ai utilisé "Pas à pas détaillé" pour suivre l'appel vers la méthode Index().

La méthode Index() appelle ensuite GetAllProducts() dans la classe ProductService (namespace P2FixAnAppDotNetCode.Services) pour récupérer la liste des produits.

Enfin, le point d'arrêt de CartSummaryViewComponent.cs ligne 12 est atteint. C'est la méthode InvokeAsync() de la classe CartSummaryViewComponent dans le namespace P2FixAnAppDotNetCode.ViewComponents. Ce composant affiche le nombre d'articles dans le panier dans la barre de navigation. J'ai utilisé "Pas à pas sortant" pour sortir rapidement de ce composant.


## 9. Déploiement Windows

J'ai utilisé la commande suivante pour générer l'exécutable Windows :

dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true

L'exécutable se trouve dans bin/Release/net10.0/win-x64/publish/

## 10. Lien vers l'exécutable

Lien Google Drive : https://drive.google.com/file/d/1qDoS_POFWycJcFeF6ZgXPSx_GzOjWOkU/view?usp=drive_link