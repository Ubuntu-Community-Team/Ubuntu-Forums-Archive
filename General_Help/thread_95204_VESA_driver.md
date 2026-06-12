---
title: "VESA driver"
date: 2005-11-26
forum: General Help
---

### Post by Fittersman on 2005-11-26
I was instructed to in the etc/X11/xorg.conf file to change my driver to vesa

Section "Device"

Identifier ...
Driver "Vesa"
BusID ...

i know ubuntu can look better and be faster. How can i change this so it still works but is high quality?

---

### Post by cdsboy on 2005-11-26
Is ubuntu running slow in the first place? what exactly are you trying to get to run faster?

---

### Post by jvictor on 2005-11-26
Please post a more detailed description of you problem, like what graphics card you have etc..

---

### Post by Fittersman on 2005-11-26
i have a Radeon 7500 video card and as far as i know ubuntu is running on the intel graphics card that is on my motherboard so i want it to use my radeon card instead.

im not sure if that will help you or not but if you need more i will tell you what you need

---

### Post by jvictor on 2005-11-29
First of all if u have the Radeon card put in the AGP slot.. That must be the one on PCI 0:0 ..and Ubuntu must use that in place of the intel one.. if thats not happening , u have to check ur bios settings if theres a way to disable the onboard graphics card. Doing so will make things fall in to place... HTH

---

### Post by Fittersman on 2005-11-29
i think its working now

---

