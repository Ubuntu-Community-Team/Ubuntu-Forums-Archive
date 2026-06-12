---
title: "Installing on dead 95"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by ryan.megatron on 2009-02-21
[COLOR="SeaGreen"]Hey everyone, I just download Ubuntu a while ago hoping I can install it on my Windows 95 computer (which doesn't really work). I tried booting up the computer and putting in the ISO CD I made but nothing happend, can anyone help me out here?[/COLOR]

---

### Post by fudoki on 2009-02-21
When you make a setup disk from an ISO image, you do not simply copy the ISO image onto the CD, it must be read onto the CD, which makes the CD (or DVD) a bootable disk.  Most CD burning programs have a "Tools" menu item that contains an option like "Create CD from ISO Image".  Use this to make your setup disk, not just Copy.

Once that's done correctly...

Go into the BIOS (the "Setup", usually F2 or on older machines Shift-F1) confirm that your BIOS battery is not dead (the date and time will be set, not 1-1-99, etc., if it is not, set the date and time, restart, go back into BIOS and see if it holds the clock settings, if not, get a new BIOS battery, else your settings will be lost every time you shut down! A real pain!) that done, make sure the system can "see" all your devices, hard disk, CD ROM, DVD, floppy, etc.  If this is good, go to your "Boot" settings and make sure your Boot Devices list has the CD or DVD you are putting the Ubuntu ISO disk into as the FIRST boot device, the hard disk should be last, don't leave any gaps in the list! (If you only have 2 boot devices the third should read "Disabled".)  Now put the Ubuntu ISO CD into the drive, select Save and Exit in your BIOS and answer "Yes", the computer re-boots and you should come up on the first page of the Ubuntu installation.

When you get this to work your old computer may well be faster and more fun than your current Winblows box...

Hope this helps, else leave a note.

fudoki

---

### Post by oldos2er on 2009-02-21
> **ryan.megatron said:**
> [COLOR=SeaGreen]Hey everyone, I just download Ubuntu a while ago hoping I can install it on my Windows 95 computer (which doesn't really work). I tried booting up the computer and putting in the ISO CD I made but nothing happend, can anyone help me out here?[/COLOR]

 What are the hardware specs?

---

