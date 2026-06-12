---
title: "Synaptic  Package Problem"
date: 2008-11-17
forum: General Help
---

### Post by gjohnno on 2008-11-17
I was attempting to download Google Earth , using a variety of suggestions such as downloading it through Mediubuntu repository , the GoogleEarthLinux.bin file. No success. 

The problem i have created is I am unable to access Synaptic Package Manager. A dialogue box pops up saying ERROR OCCURED the following details are provided " E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

As I am not all that tech savvy , what do I have to do , to correct this problem

Thank you for your assistance

---

### Post by exploder on 2008-11-17
In the terminal type, sudo dpkg --configure -a press enter, type in your password, press enter and Synaptic will work again.

---

### Post by bigbrovar on 2008-11-17
open ternimal Application/Accessories/Terminal 
then copy and paste this  ```
sudo dpkg --configure -a
``` press enter .. it would ask fior your password. give it. and enter again. should fix the problem

---

### Post by costre on 2008-11-18
I have the same problem

When I am about to install selected upgrades / applications this pops up:

```
An error occurred.
The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 
```

When I try to remedy this by running the suggested command, this appears:

```

costre@costre-desktop:~$ sudo dpkg --configure -a
[sudo] password for costre: 
Setting up ufw (0.23.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ufw (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted 
```

Suggestions?

---

### Post by tamer.solieman on 2008-11-22
i'v the same problem plz any suggestion???

---

