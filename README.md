# PHP-Essentiel

### 4 types scalaires :
* boolean       
* integer       
* float (nombre à virgule flottante, i.e. double)        
* string        
       
### 2 types composés :     
* array      
* object      

### 2 types spéciaux :
* resource     
* NULL     

## Les failles sécurités
* XSS (plus officiellement appelée Cross-Site Scripting) est une faille permettant l'injection de code HTML ou JavaScript dans des variables mal protégées.        
* Faille Include      
* Faille d'upload     
* Injection SQL      
* La CSRF      
* La CRLF      
* Vole de Session      
* Brute Force      
* DDOS

## Programation Orientée Objets
```php
  // Etendre d'une classe
  class Magicien extends Personnage {}
  // Implémenter une interface 
  class MaClasse implements iC {}
  // Les interfaces peuvent s'etendre entre elles
  interface iB extends iA {}
  
  // Appel de class
  self:: // appele la classe actuelle
  $this  // appele l'objet
  parrent::  // appele la classe parent
  static::  // appele la classe executé
  //Les attributs et méthodes statiques sont utiles lorsque l'on ne veut pas avoir besoin d'un objet pour s'en servir.
```

### Classe abstraite et interface
__Class Abstraite__ -> ```abstract``` // non instensiable     
__Méthode abstraite__ en plaçant le mot-clé ```abstract``` juste avant la visibilité de la méthode, force toutes les classes filles à écrire cette méthode.      
        
Les objets ne sont pas sauver en variable mais par identifiant, __les objets sont passés par réference__       
Le seul moyen de dupliquer un objet => ```clone```      

* Une interface représente un comportement.        
* Les interfaces ne sont autre que des classes 100% abstraites.        
* Toutes les méthodes présentes dans une interface doivent être publiques.        
* Une interface ne peut pas lister de méthodes abstraites ou finales.      
* Une interface ne peut pas avoir le même nom qu'une classe et vice-versa.      
     
Les différences entre une classe abstraite et une interface     
* Une classe abstraite peut avoir des méthodes définis alors qu'une interface non
* Une classe ne peut extends que d'une seule classe (abstraite ou non) mais peux implémenter plusieurs interfaces

### Les traits
* Les traits sont un moyen pour éviter la duplication de méthodes.
* Un trait s'utilise grâce au mot-clé ```use```.
* Il est possible d'utiliser une infinité de traits dans une classe en résolvant les conflits éventuels avec ```insteadof```.
* Un trait peut lui-même utiliser un autre trait.
* Il est possible de changer la visibilité d'une méthode ainsi que son nom grâce au mot-clé ```as```.

### Design patterns
* Un design pattern est un moyen de conception répondant à un problème récurrent.
* Le pattern factory a pour but de laisser des classes usine créer les instances à votre place.
* Le pattern observer permet de lier certains objets à des « écouteurs » eux-mêmes chargés de notifier les objets auxquels ils sont rattachés.
* Le pattern strategy sert à délocaliser la partie algorithmique d'une méthode afin de le rendre réutilisable, évitant ainsi la duplication de cet algorithme.
* Le pattern singleton permet de pouvoir instancier une classe une seule et unique fois, ce qui présente quelques soucis au niveau des dépendances entre classes.
* Le pattern injection de dépendances a pour but de rendre le plus indépendantes possible les classes.

1. Constructor Injection: meilleurs choix pour les dépendences recquises
```php
    class User
    {
      function __construct($storage)
      {
        $this->storage = $storage;
      }

      // ...
    }
```
2. Setter Injection: meilleurs choix pour les dépendances facultatives (cache par ex)
```php
    class User
    {
      function setSessionStorage($storage)
      {
        $this->storage = $storage;
      }

      // ...
    }
```
      
Un container permet de stocker tous les services d'une application et d'instancier les objets une unique fois (ou plusieurs si factory avec pimple). Le container permet de gérer facilement tous les services il suffit de l'injecter directement dans les classes pour pouvoir appeler n'importe quel service de n'importe ou.     

## PHP 7 les nouveautés
PHP 7 est plus rapide. -> PHPNG de 25% à 70%        
```<=>``` comparaison qui donne -1 0 ou 1 si plus petit, égal, plus grand 
Possibilité d'écrire des constantes privés de class ```private const URL_IMAGE = '/images'```, on y accède avec une fonction get dans la classe
Return Type Declarations & Scalar Type Hints  // pour typer les arguments les retours des fonctions (iterable)
```php
  function addition(int $a, int $b): int
  {
    return $a + $b;
  }
```
```??``` pour isset  ```$prenom = $_GET['user'] ?? 'personne'```;     
Catch Error + Execption = Throwable. 
* catch both exceptions and errors, catch \Throwable. 
* only catch exceptions, then catch \Exception. 
* only catch errors, use catch \Error.      
Multi catch-exception avec ```|```
