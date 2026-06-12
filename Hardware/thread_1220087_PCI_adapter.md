---
title: "PCI adapter"
date: 2009-07-22
forum: Hardware
---

### Post by geogur on 2009-07-22
I bought a Linksys Wireless - G only to find out support says no linux drivers available ! Can I still make this work . I can not get the cd to run , so I am on my own to fix this . Can someone help I am not able to write my own driver and fear this is what I must do . Model No. WMP54GS PCI adapter with speedbooster

---

### Post by runesvend on 2009-07-22
Take a look at *ndiswrapper*, which enables you to use Windows drivers for certain network cards in Linux. Google it and read about it, and take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=110336](http://ubuntuforums.org/showthread.php?t=110336)

---

### Post by geogur on 2009-07-23
thanks for the link it looks like someone figured it out 4 yrs ago . i will follow the link and try to fix it . thanks for the help  Although I was hoping for a linux solution emulating windows is sort of like cheating and I have t introduce my linux system to a windows driver to run my wireless network . I don`t like the solution .

---

### Post by Bucky Ball on 2009-07-23
Manufacturer installation disks are (in most cases) no more than handy mug or glass coasters, or entertaining little frisbees when it comes to Ubuntu. :)

That looks like it has the Broadcom 4306 chipset. That is probably now covered with B43 and b43-fwcutter. If so, easy. 

Plug an ethernet cable into your machine, boot to Ubuntu, you will get offered updates, takes 'em, then you will probably be made aware there are restricted drivers available for your hardware. Accept them.

One of these will be B43, specifically designed to get the Broadcom cards happening (they were once a nightmare).


You could check this out by going to a terminal (Applications->Accessories) and type this:

```
lspci
```Down near the bottom of that list somewhere you will find your card. (Broadcom 4306 will be mentioned somewhere if it is that one.)


ps: try to avoid ndiswrapper if there is ANY other way. *Extremely* problematic with Broadcom cards.

---

