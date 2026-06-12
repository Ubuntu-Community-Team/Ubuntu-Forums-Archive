---
title: "Kubuntu-Ubuntu: are there stable ATI driver packages available ?"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2009-06-22
I have both Ubuntu 8.04 and Kubuntu 9.04.

I have the restricted drivers enabled on my Ubuntu (done a while ago) but I am finding my ATI performance to be around 5 times slower then with my Windows XP.

Upon checking the installed restricted drivers on my Kubuntu, I found none.

In looking for ATI drivers for my Kubuntu, while checking forum threads here and there, I want to know, before heading further, are there stable ATI drivers ready for both Ubuntu (8.04) and Kubuntu (9.04) that I can safely install and hope to get a performance equal to what I have in Windows ?

Or is ATI still too far back because they still do not care enought about Linux ?

---

### Post by jarl on 2009-06-22
> **Browser_ice said:**
> I have both Ubuntu 8.04 and Kubuntu 9.04.

I have the restricted drivers enabled on my Ubuntu (done a while ago) but I am finding my ATI performance to be around 5 times slower then with my Windows XP.

Upon checking the installed restricted drivers on my Kubuntu, I found none.


Your card may not be supported by the ATI binary driver, ATI just removed support for several cards in the binary driver for 9.04, you may have better luck in finding a binary driver for the 8.04 system.

Take a look at 
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027)

> **Browser_ice said:**
> Or is ATI still too far back because they still do not care enought about Linux ?

I don't think that is the case, however it seems that they have a aggresive strategy for obsoleting their own products. Don't count on cards older than 2 years to be supported in the latest binary driver. This is definitely something that talks pro NVIDIA, NVIDIAS older binary drivers can be compiled for newer versions of X.org.

Jarl

---

### Post by masux594 on 2009-06-22
Unfortunately no.. With Interpid yo can use the ati restricted drivers [maybe until ati catalyst 9.3].. With jaunty instead, the ati catalyst doesn't support graphic cards before of the HD 2xxx series.. only Hd 2xxx and newer.. So, if u want to use jaunty, you must find another drivers for your ati cards..

Sysc, A

---

