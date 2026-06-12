---
title: "package"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by m3asmi on 2009-08-14
Hi

I have a package *.deb  in /var/cache/apt/archives & I which install it ;
I find way to install it  with any command if it exist 

I try 
```
 rachid@ubuntu:/var/cache/apt/archives$ sudo apt-get install ./*.deb
[sudo] password for rachid: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet .


```
thinqs in the first

---

### Post by m3asmi on 2009-08-14
> **m3asmi said:**
> Hi

I have a package *.deb  in /var/cache/apt/archives & I which install it ;
I find way to install it  with any command if it exist 

I try 
```
 rachid@ubuntu:/var/cache/apt/archives$ sudo apt-get install ./*.deb
[sudo] password for rachid: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet .


```thinqs in the first


I think this is the solutio

```
sudo dpkg -i `ls *.deb`

```

---

