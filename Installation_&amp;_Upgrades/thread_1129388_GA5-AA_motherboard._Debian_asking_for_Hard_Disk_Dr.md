---
title: "GA5-AA motherboard. Debian asking for Hard Disk Driver"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by blubaustin on 2009-04-18
I have a Debian Testing net-install disk trying to install on a:
AMD 450mhz AMD k6-II
256MB ram
NVIDIA 4200 AGP
USB cable modem
5GB IDE HD Fireball
Yamaha 16x10x40 burner IDE

and it asks for a Hard Disk driver....any ideas?

---

### Post by lemming465 on 2009-04-19
See if you can adjust BIOS settings for the IDE controller; the kernel you are loading isn't recognizing the disk controller chipset.  Do you know what the motherboard model is, and in particular what the "southbridge" chip is?

---

### Post by blubaustin on 2009-04-19
Not really any setting on the Bios except for a addon IDE card, or to set it as primary, secondary, or both. 

Southbridge: ALi M1542 A1

---

### Post by blubaustin on 2009-04-21
Also has same error on my JP vectra VL400 MT, PIII 1.0ghz, 256mb RAM, 5GB hd, ATI RAGE 128 16mb PRO AGP 4x. Which is kinda wierd...

---

### Post by cariboo on 2009-04-21
I have never seen a debian based installation ask for a hard drive driver, unless the hard drive was connected to addon card or if using Dynamic Drive Overlays to over come BIOS limitations on hard drive size.

Jim

---

### Post by lemming465 on 2009-04-22
If you are getting the same error from two different systems, how sure are you that the CD-R burned successfully?  Bad burns is probably the single most common source of problems, which is why so many CD's (Ubuntu, Fedora, Redhat Enterprise, ...) have self-test boot modes.  I can't remember, does debian have a self-test mode?  If so, does your CD pass?

---

