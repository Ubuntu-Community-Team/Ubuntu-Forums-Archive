---
title: "after kernel 2.6.35-28 upgrade the system doesn't boot in graphics mode"
date: 2011-04-29
forum: Hardware
---

### Post by fbvasconcellos on 2011-04-29
does anyone here had the same problem?

i have downloaded and install fresh kubuntu 10.10 with kernel 2.6.35-22, but after the kernel update to version 2.6.35-28 the system started to boot at console mode.

how to fix it (don't answer upgrade to 11.04 please).

---

### Post by Danchik on 2011-05-02
i've got the same problem!
actually  in was in the previous kernel update

what is strange - this kernel , 35-28 , does not update via apt-get install
but only by the KPackageKit   guy problem

---

### Post by Danchik on 2011-05-02
I saw a solution 
- apparently the headers are not installed 
sudo apt-get install linux-headers-2.6.35-28-generic 

taken from
 [http://askubuntu.com/questions/32060/2-6-35-28-kernel-update-breaks-xorg](http://askubuntu.com/questions/32060/2-6-35-28-kernel-update-breaks-xorg)


*worked for me

---

