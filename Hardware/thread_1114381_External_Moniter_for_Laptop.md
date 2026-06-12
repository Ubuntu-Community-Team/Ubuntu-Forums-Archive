---
title: "External Moniter for Laptop"
date: 2009-04-02
forum: Hardware
---

### Post by Magical Tiger on 2009-04-02
Hi and thanks in advance for any help.
I tried earlier to do it myself off of previous forums and such, but I only succeeded in screwing up my computer.
I have a Nvidia Geforce Go 7600 with the recommended driver( NVIDIA Accelerated Graphics Driver( version 177 ) [recommended] ) on a 17" Alienware laptop. I am trying to connect an Acer x223w moniter. In Ubuntu I get to the boot screen with Ubuntu loading bar on both screens, then the screen goes black and the screen for different graphics options comes up. I have tried everything so far. I am now booting into low graphics mode. If I use the default open-source driver then I can't use extra visual effects and my external moniter just goes crazy( random bars of color ). My moniter works perfectly plug and play on my Windows Vista Home Basic partition though.
Again, any help would be appreciated and thanks.

---

### Post by Magical Tiger on 2009-04-06
With no help from anyone here, I managed to fix my problem by upgrading the the Jaunty beta and using the nvidia x server configuration tool. After upgrading to Jaunty, I ran "gksu nvidia-settings" and edited what I wanted.

---

### Post by daveyllennod on 2010-01-09
I am having a similar problem, when I start the computer I can view the images from the laptop on the monitor screen, however, the signal stops bein set to the monitor when I get to the login window to access my desktop. I did get it working at one stage but it was in low graphics mode and the resolution was way off.

I have tried the following, ctrl alt F5, I get a black terminal screen. tried xconfig which has been suggested in similar posts on this topic however, my xconfig settings are rather sparse in comparison with the examples of other people xconfig settings so i havent tried editing anything as theres nothing to edit basically.

The Nvidia driver that has been mentioned quite alot is installed on my computer, (however i don't know if I have the hardware for it though), I've tried to open the configuration setings for it but the window begins to load but never opens.

Any help with sorting this out would be much appreciated, I dont have that much experience with terminals or code etc, been using ubuntu jaunty for about a year now but havent had any problems like this before so havent needed to fix anything like this.

specs are
E-systems laptop 13" screen
DGiM L--1731 external monitor

my xconfig basically consists of the empty sections that make up everyone elses xconfig so any suggestions wat to add in there would help out

dave

---

### Post by daveyllennod on 2010-01-09
correction I am now usiing Karmic Koala. Again any help would be appreciated

dave

---

