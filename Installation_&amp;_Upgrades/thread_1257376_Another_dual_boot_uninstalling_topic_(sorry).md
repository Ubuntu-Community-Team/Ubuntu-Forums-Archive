---
title: "Another dual boot uninstalling topic (sorry)"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by Colex on 2009-09-03
First of all, big salute to everyone, great minds here. :)

So... 

After a couple of years of ubuntu I've decided to go back to XP for good, and also free some space on my HDD... 

In the XP's disk menagment I've deleted the swap and ext3 partitions (they were on a different HDD than the XP's), but when I've started formatting the ext3, at 3% I've got the blue screen of death (ati2dvag, dumping memory... usual stuff on my XP machine, it's an unrisolvable problem with my graphics card)
But, after rebooting I've got:
GRUB 1.5, error 17 

(the error seems pretty frequent here, searched a lot, but still I couldn't solve it... I've tried everything...


- reinstalling ubuntu, booting from the live cd = no results, everytime the recovery console pops up...
- XP installation cd = recovery console wont start, says there is no hard disk... 
- I've got every usb storage device off

Maybe should I try restarting bios? 


**Please help, any thoughts...?  **


Cheers! :popcorn:

---

### Post by fatbotgw on 2009-09-03
Have you tried this: [http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")

---

### Post by presence1960 on 2009-09-03
you deleted the ubuntu partitions but GRUB is still in the MBR. You need to use your XP install CD to run recovery console to restore Windows to the MBR. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") and use the instructions for XP.

Until you restore XP's bootloader to the MBR GRUB will continue to look for menu.lst on the partitions you deleted. Since they don't exist you will keep getting a GRUB error.

Alternately you could try super grub disk. I believe it can restore a windows MBR.

---

### Post by Colex on 2009-09-09
> **presence1960 said:**
> you deleted the ubuntu partitions but GRUB is still in the MBR. You need to use your XP install CD to run recovery console to restore Windows to the MBR. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") and use the instructions for XP.

Until you restore XP's bootloader to the MBR GRUB will continue to look for menu.lst on the partitions you deleted. Since they don't exist you will keep getting a GRUB error.

Alternately you could try super grub disk. I believe it can restore a windows MBR.

My windows xp setup doesn't recognise any of the HDDs.

---

### Post by Colex on 2009-09-09
> **fatbotgw said:**
> Have you tried this: [http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")

I did, but the bios is kinda restricted (it wasn't before the error 17)... the only things I see are the raid HDD menu (1x250gb, 1x75gb), and a "create array" option. Nothing else.


EDIT:

I've refreshed the bios and now I have all the funcionallity... did what says on the link, and still... error 17

I've tried even to remove the connectors of the 80gb linux disk, and I've got error 21. 
Tried to repair the MBR, but windows setup doesn't recognise any hard disk...


:(

---

### Post by fatbotgw on 2009-09-10
A Windows setup disk won't recognize a drive if it doesn't have the drivers for the controller of the disk.  You don't say whether this is SATA/PATA, but I'm guessing SATA.  If it is SATA and you're dead set on using the Windows disk, you'll need to do the old "F6 to install drivers from a floppy disk" method...

Edit:

You could also try this:  [http://ubuntuforums.org/showthread.php?t=622828]("http://ubuntuforums.org/showthread.php?t=622828")

---

