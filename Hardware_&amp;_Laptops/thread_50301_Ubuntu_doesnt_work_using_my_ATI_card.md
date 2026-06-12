---
title: "Ubuntu doesnt work using my ATI card"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by dcahrakos on 2005-07-19
Well, basically ive confirmed that when starting up, it gets stuck at starting hotplug subsystem, only because of my ATI Radeon, when I switch to my onboard card, which sucks, it works, but its only 32MB, and I would like to use my radeon 9250 128MB card, so it runs better, and can run better games and stuff, is there anyway to make it work with the Radeon?

---

### Post by chaumurky on 2005-07-19
[QUOTE=dcahrakos]Well, basically ive confirmed that when starting up, it gets stuck at starting hotplug subsystem, only because of my ATI Radeon, when I switch to my onboard card, which sucks, it works, but its only 32MB, and I would like to use my radeon 9250 128MB card, so it runs better, and can run better games and stuff, is there anyway to make it work with the Radeon?[/QUOTE]
 Strange, that's my model. I had no problems installing it. Perhaps there is a BIOS setting you missed? I know I had to disable the onboard video for my card to work. Just to be safe have you had the card working elsewhere recently?

---

### Post by dcahrakos on 2005-07-19
[QUOTE=chaumurky]Strange, that's my model. I had no problems installing it. Perhaps there is a BIOS setting you missed? I know I had to disable the onboard video for my card to work. Just to be safe have you had the card working elsewhere recently?[/QUOTE]
 I use windows XP also, and it works fine, and if my video card is enabled in my bios, it disables my onboard one...so i dont see the problem...its very weird

its a PCI card if that makes any difference.

---

### Post by chaumurky on 2005-07-19
[QUOTE=dcahrakos]I use windows XP also, and it works fine, and if my video card is enabled in my bios, it disables my onboard one...so i dont see the problem...its very weird

its a PCI card if that makes any difference.[/QUOTE]
 Really, PCI? Mine's AGP so there may be a difference there. XP pays little attention to many BIOS settings so you can get away with misconfiguration more often. I don't know if that applies in this case. My BIOS has a "Primary VGA boot device (PCI/AGP)" or something to that effect - that wasn't automatically changed. Unfortunately, that's all I have to offer. Sorry.

---

### Post by dcahrakos on 2005-07-20
[QUOTE=chaumurky]Really, PCI? Mine's AGP so there may be a difference there. XP pays little attention to many BIOS settings so you can get away with misconfiguration more often. I don't know if that applies in this case. My BIOS has a "Primary VGA boot device (PCI/AGP)" or something to that effect - that wasn't automatically changed. Unfortunately, that's all I have to offer. Sorry.[/QUOTE]
 thats the way I switch over to onboard, setting the primary VGA boot to onboard...

---

### Post by ATIuser on 2007-11-30
I too am having the same problem. After installing via the on-board card, I noticed the ATI was recognized and had a driver installed for it. So, I figured the driver from the installation was corrupt so I uninstalled the fglrx driver and I tried the installation instructions for the open source driver and it still hangs. I've tried to install the proprietary driver following the instructions from the linux wiki but when I go to create the package, I am given a Syntax error in regards to the installation file. Don't know what to do there. My card is read as a Radeon 9250 in windows XP, Gutsy reads it as a 9200 pro. 

Is there a file somewhere that specifies which drivers to load on boot up?

---

