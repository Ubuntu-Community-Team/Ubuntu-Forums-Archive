---
title: "Can anybody help me with ubuntu 10.10?"
date: 2011-04-11
forum: Hardware
---

### Post by rccp on 2011-04-11
hello, i have recently bought a new pc but i can't find a way to install ubuntu 10.10 correctly or maybe i'm not doing things ok well i have: a core i3-540, motherboard foxcon h55xmv, 4  gb ram, intel integrated graphics and a 500 gb hard disk well the thing is that ubuntu doesn't recognizes the integrated graphics so i enter not in gnome graphic mode but in terminal mode, how do i solve it? or maybe i should install ubuntu 10.10 32 bits?
also would i be able to run compiz with this pc? 

any help i appreciate thanks

---

### Post by washakie on 2011-04-11
How are you trying to install Ubuntu? Is there an OS already installed on your machine? Are you using a CD or USB?

---

### Post by coffeecat on 2011-04-11
> **rccp said:**
> intel integrated graphics and a 500 gb hard disk well the thing is that ubuntu doesn't recognizes the integrated graphics

It's unusual for Ubuntu to have problems with Intel graphics (unless very old). The main exception is the so-called "Poulsbo" GMA500, which is problematic. Do you know exactly which Intel integrated graphics you have?

---

### Post by rccp on 2011-04-11
> **washakie said:**
> How are you trying to install Ubuntu? Is there an OS already installed on your machine? Are you using a CD or USB?
yes another os is already installed, win 7 64 bits and is working perfectly without issues, and i used a usb for the install

---

### Post by rccp on 2011-04-11
> **coffeecat said:**
> It's unusual for Ubuntu to have problems with Intel graphics (unless very old). The main exception is the so-called "Poulsbo" GMA500, which is problematic. Do you know exactly which Intel integrated graphics you have?
well its Intel® HD Graphics the one that comes with the procesor so i really don't understand why it doesnt work with ubuntu 10.10.

also i tried to do a sudo aptitude full-upgrade to see if it downloads a driver or something but it didn't work the screen turn black after 5 mins i press enter

---

### Post by rccp on 2011-04-11
> **coffeecat said:**
> It's unusual for Ubuntu to have problems with Intel graphics (unless very old). The main exception is the so-called "Poulsbo" GMA500, which is problematic. Do you know exactly which Intel integrated graphics you have?
well its Intel® HD Graphics the one that comes with the procesor so i really don't understand why it doesnt work with ubuntu 10.10.

also i tried to do a sudo aptitude full-upgrade to see if it downloads a driver or something but it didn't work the screen turn black after 5 mins i press enter

---

### Post by coffeecat on 2011-04-11
> **rccp said:**
> well its Intel® HD Graphics the one that comes with the procesor so i really don't understand why it doesnt work with ubuntu 10.10.

There are many different varieties of Intel integrated graphics.

[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

What does Windows say it is?

---

### Post by rccp on 2011-04-11
well this is what i got from everest
 
Device Description Intel(R) HD Graphics
Adapter String Intel(R) HD Graphics
BIOS String Intel Video BIOS
Chip Type Intel(R) HD Graphics (Core i3)
DAC Type Internal
Memory Size 1338940 KB
 
and well i guess it's the (GMA HD)

---

### Post by rccp on 2011-04-11
hey i managed to fix it, i entered in recovery mode and from that i used ubuntu with really low graphics, it seems that the intel HD graphics chipset package was not in ubuntu 10.10 by default so all you have to do is enter in recovery mode and apply a sudo aptitude full-upgrade to install the package

thanks a lot

---

