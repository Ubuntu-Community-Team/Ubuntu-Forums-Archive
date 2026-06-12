---
title: "Almost Done Averatec 5400 Wireless"
date: 2004-12-14
forum: Hardware &amp; Laptops
---

### Post by Averatec5400 on 2004-12-14
Other than getting video driver support (other than VESA) I am almost done with my laptop setup.

I just need to get the ralink 2500 wireless card working.

They have some ver new GPL drivers at [www.ralinktech.com](www.ralinktech.com) but I can't seem to get the kernel modules to compile (I followed a MEPIS howto somewhat, of course making the needed changes for my 686 kernel instead)

Has anyone else gotten this working?



BTW, The video drivers for this (via unichrome pro) that I have found on this forum seem to "work" but I just have a sharp black display, I can hear the intro sounds and everything, no odd output in X logs (still on warty, not gone to xorg and hoary yet)

---

### Post by Averatec5400 on 2004-12-15
[QUOTE=Averatec5400]Other than getting video driver support (other than VESA) I am almost done with my laptop setup.

I just need to get the ralink 2500 wireless card working.

They have some ver new GPL drivers at [www.ralinktech.com](www.ralinktech.com) but I can't seem to get the kernel modules to compile (I followed a MEPIS howto somewhat, of course making the needed changes for my 686 kernel instead)

Has anyone else gotten this working?



BTW, The video drivers for this (via unichrome pro) that I have found on this forum seem to "work" but I just have a sharp black display, I can hear the intro sounds and everything, no odd output in X logs (still on warty, not gone to xorg and hoary yet)[/QUOTE]
 I take it not too many read this :(

---

### Post by Averatec5400 on 2004-12-18
[QUOTE=Averatec5400]Other than getting video driver support (other than VESA) I am almost done with my laptop setup.

I just need to get the ralink 2500 wireless card working.

They have some ver new GPL drivers at [www.ralinktech.com](www.ralinktech.com) but I can't seem to get the kernel modules to compile (I followed a MEPIS howto somewhat, of course making the needed changes for my 686 kernel instead)

Has anyone else gotten this working?



BTW, The video drivers for this (via unichrome pro) that I have found on this forum seem to "work" but I just have a sharp black display, I can hear the intro sounds and everything, no odd output in X logs (still on warty, not gone to xorg and hoary yet)[/QUOTE]
 Well I have made some progress using ndiswrapper, I can do anything I want on my internal network but get nowhere with the external, seems like an issue with route, I read all the FAQ/help on ndiswrapper and it didn't work, so progress, but not complete.

---

### Post by Averatec5400 on 2004-12-19
[QUOTE=Averatec5400]Well I have made some progress using ndiswrapper, I can do anything I want on my internal network but get nowhere with the external, seems like an issue with route, I read all the FAQ/help on ndiswrapper and it didn't work, so progress, but not complete.[/QUOTE]
 Done, got it, about to write a mini howto for other curious rt2500 users with ubuntu

edit: oh I am posting wirelessly now!

---

### Post by jak on 2004-12-19
hi, im having a very similar problem just not on a laptop. im sure your 'how to' will come in handy :D

edit: im sorted too. ndiswrapper proves very handy!

---

### Post by Averatec5400 on 2004-12-19
[QUOTE=jak]hi, im having a very similar problem just not on a laptop. im sure your 'how to' will come in handy :D

edit: im sorted too. ndiswrapper proves very handy![/QUOTE]
 yea if you play with ndiswrapper enough you will get it.

I should have something together in next few days.

---

