---
title: "Drivers for nvidia 9600GT"
date: 2008-05-05
forum: Hardware
---

### Post by ali999 on 2008-05-05
Hi

I bought an nvidia 9600gt card for my computer today but for the life of me, I cannot find the proper drivers for it to allow me to enable compiz and other 3D applications. I have tried several other websites and it seems that a lot of people are having issues with this one. I found some help here: [http://ubuntuforums.org/showthread.php?t=766622&highlight=nvidia+9600gt+drivers+hardy&page=2](http://ubuntuforums.org/showthread.php?t=766622&highlight=nvidia+9600gt+drivers+hardy&page=2) where one of the posts have instructions that the person says worked for him. However when I try the commmand sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev i get an error saying the package linux-header does not exist or something to that effect. Can someone please give a definative guide to this? The card is made by ASUS if it matters, but they're website only contains windows drivers. Nvidia website was not much help either. Only reason I bought an nvidia card was cuz i thought linux support for it was supposed to be good. PLEASE HELP!!!

---

### Post by ali999 on 2008-05-06
anyone?

---

### Post by ali999 on 2008-05-06
ok then..i think i solved my own problem

[http://www.nvnews.net/vbulletin/showthread.php?t=109422](http://www.nvnews.net/vbulletin/showthread.php?t=109422)

---

### Post by ali999 on 2008-05-06
Ps: if u get an error saying something like "YOU DON'T APPEAR TO HAVE LIBC HEADER FILES INSTALLED ON YOUR COMPUTER. YOU MUST INSTALL DISTRIBUTION LIBC DEVELOPMENT PACKAGE FIRST". Then do this first: sudo apt-get install build-essential xorg-dev pkg-config linux-headers-$(uname -r)

---

### Post by katon on 2008-10-25
> **ali999 said:**
> ok then..i think i solved my own problem

[http://www.nvnews.net/vbulletin/showthread.php?t=109422](http://www.nvnews.net/vbulletin/showthread.php?t=109422)


how is you 9600gt card? Is it a noisy cooler or with the driver is good enough?

---

### Post by alankatana on 2010-05-27
Well I have the black screen....no idea  what to do...no opportunity to load drivers or anything....how can this have been overlooked in such a major release....???


Alan

---

