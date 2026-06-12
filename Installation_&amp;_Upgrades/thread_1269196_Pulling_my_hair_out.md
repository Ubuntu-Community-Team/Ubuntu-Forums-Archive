---
title: "Pulling my hair out"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by StoopidPyro on 2009-09-17
I have an Asus eee 1005hab.  I've been trying to get the wireless and wired to work.  I simply have to compile a new kernel, (2.6.30).  - But, in order to do that, I have to have the application "patch" installed.  When I use 'apt-get install patch' the process starts up fine, except, it asks for the cd..  I don't have the cd, since i used an ISO, on a seperate windows partition to install it.  I obviously cant install it off the internet, because i'm trying to get the internet in the first place.  No matter what i do, i can't mount a flash drive as a cdrom.  When i attempt to mount the iso as a cdrom, it appears as a cdrom, but the "patch" installation just doesn't detect it.  Does anyone have any tips to help me out?  I just want my wireless to work!

---

### Post by StoopidPyro on 2009-09-18
nevermind, i figured it out. 
 
i did:
 
mount -o loop 'image.iso' /cdrom
 
 
boom. done.  what a great way to start my membership with such a noob question. lol

---

### Post by running_rabbit07 on 2009-09-18
You may need to go to System>Administration>Software Sources and check the boxes for archive.canonical.com like in my screenshot. If by any chance there are any selections for ISOs or CDs then you need to uncheck them.

---

