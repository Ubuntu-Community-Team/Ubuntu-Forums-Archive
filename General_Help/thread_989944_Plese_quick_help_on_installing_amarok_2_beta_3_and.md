---
title: "Plese quick help on installing amarok 2 beta 3 and mono 2 on ubuntu"
date: 2008-11-22
forum: General Help
---

### Post by ravindukelum on 2008-11-22
how to install amarok 2 beta 3 and mono 2 on ubuntu 8.10 please help me

---

### Post by Phreaker on 2008-11-22
For amarok:
download the tarball: [http://download.kde.org/download.php?url=unstable/amarok/1.94/src/amarok-1.94.tar.bz2](http://download.kde.org/download.php?url=unstable/amarok/1.94/src/amarok-1.94.tar.bz2)

And follow these instructions: [http://amarok.kde.org/wiki/Compiling:2.0](http://amarok.kde.org/wiki/Compiling:2.0)

For mono:
Paste this to firefox adress bar: 
apt:mono-2.0-devel

---

### Post by ravindukelum on 2008-11-22
[QUOTE=Phreaker;6228862]For amarok:
download the tarball: [http://download.kde.org/download.php?url=unstable/amarok/1.94/src/amarok-1.94.tar.bz2](http://download.kde.org/download.php?url=unstable/amarok/1.94/src/amarok-1.94.tar.bz2)

And follow these instructions: [http://amarok.kde.org/wiki/Compiling:2.0](http://amarok.kde.org/wiki/Compiling:2.0)

Then I got this error how to solve this

CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/ravindu/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:8 (find_package)


-- Configuring incomplete, errors occurred!

---

### Post by directhex on 2008-11-22
> **Phreaker said:**
> For mono:
Paste this to firefox adress bar: 
apt:mono-2.0-devel

That provides development packages for CLR 2.0 (i.e. .NET 2.0+ compatible), not Mono 2.0 (Intrepid has 1.9.1)

---

### Post by trooperchix on 2009-02-19
I have typed 

[apt:mono-2.0-devel]("apt:mono-2.0-devel")

and nothing really happens.  What am I missing?  I'm trying to install "Tracker Checker"  any help would be lovely.

---

