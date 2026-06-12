---
title: "XFi Install Errors..."
date: 2009-06-11
forum: Hardware
---

### Post by Hdusten on 2009-06-11
Hey Guys

First of I'm somewhat new to Ubuntu and Linux in general so bear with me ;)

First off the Error that appears when I try to make 

make: *** /lib/modules/2.6.28- 11 - server/build: No such file or directory. Stop.
make: *** [all] Error 2

Haha me being a noob, I have no clue what this means.

Any help would be greatly appreciated

---

### Post by Hdusten on 2009-06-11
So I've been tinkering, I believe my problem is that when i run make it is searching for the build directory in -server when in fact it's located in -generic how do I go about getting make to look in the -generic build directory

---

### Post by Hdusten on 2009-06-11
So i just copied the build directory over and managed to get it to make, although now won't install

FATAL: Error inserting ctxfi (/lib/modules/2.6.28-11-server/kernel/drivers/ssound/ctxfi.ko): Invalid module format
make: *** [install] Error 1

Assuming the first step went wrong

---

