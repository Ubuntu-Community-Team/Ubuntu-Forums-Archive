---
title: "Unable to install KMess in Ubuntu 8.10"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Cocotaso on 2009-01-28
I am extremely new to the Linux world. I've had some experience back in college but have forgetten many!

I am trying to install KMess ([http://www.kmess.org/](http://www.kmess.org/)) for UBuntu 8.10 but i keep getting an error message

Opened terminal and ran the following command as per instruction

$ bash kmess-1.5.1.x86.package 

Checking for required C library versions ... OK
Checking for K Desktop Environment (Libraries) ... failed

Error: Could not find 'K Desktop Environment (Libraries)'. Try using the native package manager for Ubuntu 8.10 (apt-get) to install a package with similar name to 'kdelibs'.

Error: Unable to prepare package KMess.

Please help. Thank YOu

---

### Post by Partyboi2 on 2009-01-28
kmess is in the ubuntu repos. You can install by searching for kmess in Synaptic or you can open a terminal and type
```
sudo apt-get install kmess
```Edit: If you need to compile for some reason you can install the dev packages required by
```
 sudo apt-get build-dep kmess
```

---

### Post by Cocotaso on 2009-01-30
PROBLEM SOLVED! Thanks for taking the time ...

---

