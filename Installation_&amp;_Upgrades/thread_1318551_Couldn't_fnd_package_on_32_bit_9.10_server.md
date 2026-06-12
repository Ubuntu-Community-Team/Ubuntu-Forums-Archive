---
title: "Couldn't fnd package on 32 bit 9.10 server"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by fieldway on 2009-11-07
Hi

This my first time here.


I install Karmic Koala 32 bit server  without any problems.  But when I try to install some package like Moodle, Drupal6, Python-moinmoin by using the command sudo apt-get install (package name)
It come back saying "E: Couldn't find package".

Any help to solve this would be great

Thanks

---

### Post by mac9416 on 2009-11-07
Hey, fieldway,

Package names are never capitalized. If you run 'sudo apt-get install python-moinmoin' or 'sudo apt-get install moodle' it should work.

Good luck!

---

### Post by fieldway on 2009-11-07
> **mac9416 said:**
> Hey, fieldway,

Package names are never capitalized. If you run 'sudo apt-get install python-moinmoin' or 'sudo apt-get install moodle' it should work.

Good luck!
Thanks for that.  Just try that and same error message appear.

Just noticed the message also say 
Reading package list ...  Done
Building dependency tree
Reading state information ... Done
E: Couldn't find package moodle

---

### Post by mac9416 on 2009-11-07
It works OK for me. Have you enabled all official repos? Also, perhaps if you run 'sudo apt-get update' first it will work.

---

