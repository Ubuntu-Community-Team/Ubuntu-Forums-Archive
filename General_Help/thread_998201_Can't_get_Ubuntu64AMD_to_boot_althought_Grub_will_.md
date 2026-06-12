---
title: "Can't get Ubuntu64AMD to boot althought Grub will let XP Boot Fine"
date: 2008-11-30
forum: General Help
---

### Post by marti972 on 2008-11-30
I used the live disk 8.10 to set up my XP system to dual boot. Now I have both systems installed. Grub offers me all the options, XP boots fine. But, Ubuntu just goes to a blink cursor.

1. I'm using 64bit AMD. The live disk has the same problem but rarely.

2. My video card is a Matrox G450. I booted up with the live disk and used the installer to install the driver, for same, but does it really install it to my Ubuntu installation even when I'm using the live disk to operate. It didn't help.

3. The Ubuntu 32 bit live disk works just fine.

4. I tried pci=noacpi, didn't help.

Help please, I'm stuck with Windows.

---

### Post by mdurham on 2008-11-30
have you tried booting with 'noapic' as well?

---

### Post by zeigfried on 2008-11-30
Hey,

Just a long shot, but try to log in Recovery Mode, see if you are able to fall back to a root terminal.
If you managed to do that, reboot, again in recovery mode, and try the options to fix X and packages... See if you can boot. 
If you can't we should take a look at some of the logs in /var/.

Cheers

---

### Post by marti972 on 2008-11-30
mdurham - I misspelled "noapic" duh. I try that now.

---

