---
title: "virtual package?"
date: 2008-11-11
forum: General Help
---

### Post by tostrye on 2008-11-11
I am trying to install Cinelerra. I have done everything that [http://cinelerra.org/getting_cinelerra.php#gutsy](http://cinelerra.org/getting_cinelerra.php#gutsy) tells me, but i get the following output:

> leroy@leroy-desktop:~$ wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Get:2 [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy Release.gpg [197B]
Ign [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy/main Packages
Fetched 2B in 0s (4B/s)  
Reading package lists... Done
leroy@leroy-desktop:~$ sudo aptitude update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Get:2 [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy Release.gpg [197B]
Ign [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-gutsy/main Packages
Fetched 2B in 0s (4B/s)  
Reading package lists... Done
leroy@leroy-desktop:~$ sudo aptitude install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  cinelerra 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1180B of archives. After unpacking 4096B will be used.
The following packages have unmet dependencies:
  cinelerra: Depends: cinelerracv which is a virtual package. or
                      cinelerrahv which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.


---

