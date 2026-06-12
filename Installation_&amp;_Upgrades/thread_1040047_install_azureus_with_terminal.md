---
title: "install azureus with terminal"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by tsakalaki on 2009-01-15
hello. I am using ubuntu 8.04 at the university of Ioannina,Greece. I want to install azureus 3.0.4.2, but i can't. Can anyone help me? I would like to install with the terminal because I looked in the internet and in some forums they say that the installation should be done using software something, but probably the administrator in the lab isn't allowing to do it.

---

### Post by Partyboi2 on 2009-01-15
If you want to use the one if the Ubuntu repo you can open a terminal and type
```
sudo apt-get install azureus
```Or for a later version download from [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)
then asumming you downloaded it to your Desktop
```
cd ~/Desktop
```then extract it
```
tar xvjf Vuze*
```then enter source directory
```
cd vuze
```then run it using
```
./azureus
```

---

### Post by Tim Sharitt on 2009-01-15
You should be able to install with apt-get
```
sudo apt-get install azureus
```
However, you will nee administrator priviledges on your account to install it.

---

### Post by tsakalaki on 2009-01-15
> **Tim Sharitt said:**
> You should be able to install with apt-get
```
sudo apt-get install azureus
```
However, you will nee administrator priviledges on your account to install it.

and if i don't have? What sould I do?

---

### Post by Tim Sharitt on 2009-01-15
Find an admin to install it for you.

---

