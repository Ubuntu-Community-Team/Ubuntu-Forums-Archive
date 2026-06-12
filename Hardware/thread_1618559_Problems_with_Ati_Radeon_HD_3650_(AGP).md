---
title: "Problems with Ati Radeon HD 3650 (AGP)"
date: 2010-11-10
forum: Hardware
---

### Post by Destructo47 on 2010-11-10
I recently bought a new video card; the  Ati Radeon HD 3650, which is an AGP card.  It goes in the slot fine, and I have enough juice in the power supply to use it.  However, I have ran into some problems trying to use it.  First of all, I'm confused with which driver to use.  I installed the proprietary driver, but that didn't really help.  The card has 512 MB of DDR2 RAM on it, but acts like my previous 64 MB card.  The box promises "the ultimate high definition experience", but yet it lags on HD videos and higher-end games, even at lower resolutions.

I looked in the BIOS setup, and I can't change anything about the installed video card.  All I can change is if the preferred video card is PCI or AGP, and some memory settings with the onboard graphics.  I have heard that AMD is not very friendly with Linux.  Is that true?

Ubuntu 10.04 Lucid Lynx
Kernel version: 2.6.32-25-generic
Intel Pentium 4 Dual Core HT 2.4 GHz
Mobo: Intel D865GLC/D865PE50
BIOS Version: 010.085.000.001.000000
1.5 GB DIMM RAM
Ati Radeon HD 3650
     512 MB DDR2 RAM 400 MHz
     725 MHz Clock
     AGP x8
Ati Catalyst Version 10.10

---

### Post by jrave on 2010-11-10
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide") Should help you install the correct driver for your system. 

I'm not extremely knowledgeable in this field, but I do no that your card has some power management settings which alter the performance output of the card to scale with power consumtion. I'm unsure how to get this to work with linux - in fact, I'm here looking for an answer to a similar problem - but I think this is probably the direction you want to look in.

---

### Post by Destructo47 on 2010-11-15
Thank you.  I'll take a look and post any results.

---

### Post by Destructo47 on 2010-11-16
I tried installing the edge driver and it actually performed WORSE than the proprietary CatalystTM driver. I tried to uninstall it, but apparently the system didn't remove it.  I tried to reactivate the CatalystTM driver, and upon reboot the system hangs at the purple Ubuntu screen.  I have tried removing the video card and switching to onboard to fix it, but my screen will always say "No Signal".  I'm not going to start a new thread, but could someone point me to a thread or website that shows how to remove a secondary video driver?  I Googled it all to no avail. :cry:  I appreciate your help, jrave, but nothing on that page really helps. I think the main problem here is a lack of good Linux support from AMD.  The drivers they provide do not allow the video card to perform like it should.

---

### Post by Destructo47 on 2010-11-21
Just a thought: would getting a larger power supply take away the performance cap? I only have 380 Watts.
Anyways, I'm just going to return this card and get an nVidia card. They tend to be more compatible with Ubuntu than Ati.

---

