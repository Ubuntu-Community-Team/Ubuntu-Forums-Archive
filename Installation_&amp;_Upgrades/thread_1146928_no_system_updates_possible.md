---
title: "no system updates possible"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by janvi on 2009-05-03
have installed Hardy Heron (V8.04 German Version) at my Dell Laitude D600 and most things works fine except: 

The update system indicates 375 available updates. If I try to execute, the system displays a list of packages to update. Unfortunately, the "install" button takes inifinite time and nothing happens. If I interrupt  the next day there no updates happened and I do not know what is going on. It seems, e.g. the predefined server location is not available and there is no message about.

---

### Post by overdrank on 2009-05-03
> **janvi said:**
> have installed Hardy Heron (V8.04 German Version) at my Dell Laitude D600 and most things works fine except: 

The update system indicates 375 available updates. If I try to execute, the system displays a list of packages to update. Unfortunately, the "install" button takes inifinite time and nothing happens. If I interrupt  the next day there no updates happened and I do not know what is going on. It seems, e.g. the predefined server location is not available and there is no message about.

Hi and welcome, you may try and update via the terminal. The terminal is located under applications, accessories. Then you can enter the command 
```
sudo apt-get update && sudo apt-get upgrade
```
Then you will enter your password and do not worry if it is not shown when typing. 
You may copy and paste the command. Then post back with any errors.

---

### Post by janvi on 2009-05-03
What I can see: It seems a problem with the destination Hayabusa what is the computer name to update: 


bosch@Hayabusa:~$ sudo apt-get update && sudo apt-get upgrade
sudo: unable to resolve host Hayabusa
[sudo] password for bosch: 
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-de 
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release.gpg                
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Translation-de [90,5kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-de
.......

assume all, the update seems to proceed succesfully and as a result the graphical version now is also fine.

---

