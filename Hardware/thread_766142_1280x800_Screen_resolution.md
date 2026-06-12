---
title: "1280x800 Screen resolution"
date: 2008-04-25
forum: Hardware
---

### Post by ubuntuubuntu on 2008-04-25
I have just installed Ubuntu 8.04 in my laptop. Its monitor is "15.4" WXGA High-Definition Brightview Widescreen Display". I have struggled to configure Ubuntu to fill up the screen with resolution 1280x800. I have searched the web, tried many solutions but it didn't work. Can someone teach me to change the resolution to 1280x800?

Thanks!

---

### Post by FredB on 2008-04-25
If you have an ATI or Nvidia GPU in your laptop, just install the "official" hardware driver using restricted driver manager.

Resolution will be the good one after install and reboot.

---

### Post by Yaywalter on 2008-04-25
Hmm, odd. I've never had a problem with Ubuntu regarding my laptop's 1280x800 screen. My laptop has an ATI card, fyi

---

### Post by HunterThomson on 2008-04-25
I was installing Ubuntu on a friends desktop with a vewsonic wide screen and when I popped in the live cd and just picked the top option to boot from the live cd it didn't fill up the screen i.e. left black on both sides of the screen. Then I tried "boot with safe graphics mode" and it filled the screen and looked grate then I installed by clicking the install desktop icon and all is well. I always thought safe graphics mode just used really crappy graphics but it seems to take more cues from the computer to help it detect the proper settings.

---

### Post by hiddensphinx on 2008-04-25
Yeah my Compaq V2000 laptop with an ATI X200 card is also busted after Hardy Herror install.

Can't get full 1280 X 800 res either :(

restricted ATI driver gets dumped after reboot!

---

### Post by tckrockz on 2008-04-25
Same Problem here with 1024 resolution...

---

### Post by amireldor on 2008-04-29
I have a laptop display that shows only 1024x768 instead of 1280x800. I even tried the ```
nvidia-settings
``` package but it didn't show a higher resolution than 1024... :(

It must be something with the xorg.conf but I don't know what.

---

