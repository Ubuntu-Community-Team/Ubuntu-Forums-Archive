---
title: "Error message in synaptic package manager"
date: 2005-11-29
forum: General Help
---

### Post by DiscoKiller on 2005-11-29
Anyone know what this means and how i fix it???

The Following errors were found on your system

E: lilypond-data: subprocess post-installation script returned error exit status 1

---

### Post by Xian on 2005-11-29
In the future you really need to try posting all of the error message. 
However, I believe this will fix your problem:

$ sudo apt-get install tetex-bin
$ sudo dpkg --configure -a

---

### Post by DiscoKiller on 2005-12-01
Thanks thats sorted the problem. but for the record, that was the full error message.

---

