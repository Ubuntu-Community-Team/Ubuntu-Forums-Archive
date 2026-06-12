---
title: "Messed up GRUB; need help."
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2009-06-03
I have a dual boot Ubuntu/XP PC. Ubuntu is 1st on the GRUB boot list & that HDD is also 1st boot in BIOS.

So, here's what happened. I was given an external HDD that was formatted for Mac. I needed to reformat for NTFS. Somehow I couldn't do this in either Windows or Ubuntu using Gparted. So, I put the XP install disk in & went into it as if I was installing XP. I select the external HDD to format to NTFS. After it finished, it started installing XP. I thought it would pause 1st, so I panicked & hit Esc. Well, it must of erased something in GRUB because after it rebooted all it said after POST was... "A disk read error occurred. Press ctrl+alt+del to restart."

After thinking a bit I changed the HDD boot order in BIOS to the XP drive so now, at least, XP does boot.
 
So, is there a way to re-write GRUB to restore the previous GRUB; like a repair CD for Ubuntu? Or, maybe GRUB writing software that acts like it does during the install process?
 
Another possible solution world be to install another version of Ubuntu on a portion of that same HDD & let it write a new GRUB. There would be 2 Ubuntu & one XP in the menu. Then, navigate to the damaged GRUB & re-write it back to the way it was. Would that be the simplest solution?

Truth is, I'm not sure what happened but it would seem something happened to GRUB.
Please advise,
George

---

### Post by brayden13 on 2009-06-03
You can install GRUB from your Ubuntu Live CD in live cd mode if you just follow simple instructions on how to do it, i had them written down but lost them. I got the commands from some thread.
This one: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

It has some commands in teh second post on it, Good luck!

---

### Post by presence1960 on 2009-06-03
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

---

### Post by GARoss on 2009-06-03
After reading 
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113) 
I'm now sure what to do. There are many options but as I'm not sure what exactly happened, I'm not sure which approach to take. 

Is a root problem or GRUB or both. There must be a way to anylize what changed after I formatted the external HDD & stopped the XP install process.

---

### Post by GARoss on 2009-06-03
brayden13 & presence1960,
I'm downloading a new copy of Ubuntu 9.04-amd64 (can't find the alpha version) & will try this. Hope it works!;)

---

### Post by GARoss on 2009-06-03
It works! When I typed "find /boot/grub/stage1" it gave me (hd0,2) & (hd0,5). I tried (hd0,2) 1st & after rebooting, it went into Ubuntu 8.10! I had forgotten that was installed way back when! Redid the process but this time used (hd0,5) & went into 9.04.

Great pointers. Thanks for you help!
George

---

### Post by presence1960 on 2009-06-03
Glad you got it working. Enjoy Ubuntu!

---

### Post by presence1960 on 2009-06-05
> **GARoss said:**
> Is a root problem or GRUB or both. There must be a way to anylize what changed after I formatted the external HDD & stopped the XP install process.

Windows probably installed it's bootloader prior to the abort in the install process. If this happened then GRUB was overwritten on the MBR. All you did was restore GRUB.

---

