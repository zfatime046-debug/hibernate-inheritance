# Hibernate Inheritance Strategies (JPA)

## Description

Ce projet démontre l'utilisation de **Hibernate ORM avec JPA** pour implémenter les différentes **stratégies d’héritage** dans une application Java.

Le projet illustre comment Hibernate gère les relations d’héritage entre classes et comment les tables sont générées automatiquement dans la base de données.

Trois stratégies d'héritage sont implémentées :

* SINGLE_TABLE
* JOINED
* TABLE_PER_CLASS

La base de données utilisée est **H2 Database (in-memory)**.

---

# Technologies utilisées

* Java
* Hibernate ORM
* JPA (Java Persistence API)
* Maven
* H2 Database

---

# Structure du projet

```
src
 └── main
     └── java
         └── com.example
             ├── model
             │
             ├── joined
             │     ├── Employe
             │     ├── Developpeur
             │     └── Manager
             │
             ├── singletable
             │     ├── Vehicule
             │     ├── Voiture
             │     └── Moto
             │
             └── tableperclass
                   ├── Produit
                   ├── Livre
                   └── Electronique

resources
 └── META-INF
      └── persistence.xml
```

---

# Configuration Hibernate

Fichier : `persistence.xml`

Connexion base de données H2 :

```
jdbc:h2:mem:testdb
```

Configuration principale :

```
hibernate.hbm2ddl.auto = create-drop
hibernate.show_sql = true
hibernate.format_sql = true
```

---

# Stratégies d’héritage implémentées

## 1️⃣ SINGLE_TABLE

Classes :

* Vehicule
* Voiture
* Moto

Hibernate crée **une seule table :**

```
vehicules
```

avec une colonne discriminante :

```
type_vehicule
```

Exemple :

```
Voiture{id=1, marque='Renault', modele='Clio'}
Moto{id=3, marque='Honda', modele='CBR'}
```

---

## 2️⃣ JOINED

Classes :

* Employe
* Developpeur
* Manager

Tables générées :

```
employes
developpeurs
managers
```

Les classes enfants sont liées à `employes` par une **clé étrangère**.

---

## 3️⃣ TABLE_PER_CLASS

Classes :

* Produit
* Livre
* Electronique

Tables générées :

```
livres
electroniques
```

Chaque classe possède **sa propre table**.

---

# Exemple de données créées

## Véhicules

```
Voiture{id=1, marque='Renault', modele='Clio'}
Voiture{id=2, marque='Peugeot', modele='308'}
Moto{id=3, marque='Honda', modele='CBR'}
```

---

## Employés

```
Developpeur{id=1, nom='Dupont'}
Developpeur{id=2, nom='Martin'}
Manager{id=3, nom='Dubois'}
```

---

## Produits

```
Livre{id=1, nom='Le Seigneur des Anneaux'}
Livre{id=2, nom='Harry Potter'}
Electronique{id=3, nom='Smartphone Galaxy S21'}
```

---

# 🎥 Vidéo d'exécution du projet

La vidéo montre :

* le lancement de l'application
* la création automatique des tables Hibernate
* l'insertion des données
* les requêtes SQL générées
* les résultats affichés dans la console

👉 Voir la vidéo :

# Résultat

Le projet démontre :

https://github.com/user-attachments/assets/4832af88-1afb-4d66-a331-230acc4fe387


* l'utilisation de Hibernate avec JPA
* les stratégies d’héritage
* la génération automatique des tables
* les requêtes SQL générées par Hibernate
