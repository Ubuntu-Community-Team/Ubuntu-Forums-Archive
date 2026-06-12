---
title: "Windows overwrites MBR every time it boots."
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by Isfria on 2006-02-05
I have just recently installed Windows on my dual boot system.

My OS drive (hda) has partitions:
0: Ubuntu Linux - Breezy Badger - (Including Boot)
1: Windows XP (SP2)
2: Linux Swap

I rebuilt Grub on my MBR using the Ubuntu install CD (had troubles using the live CD, grub wouldn't write to the MBR - no error message, but nothing changed). I used 1st post at [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)
to achieve this.

I booted up fine, went into linux fine, went into windows and it froze on the grub display showing that it was loading XP, then I rebooted and windows just loaded up, no grub, no nothing. This is all that happens now.

I repeated the entire process and the same thing happened. It seems windows is somehow checking the MBR when it loads, and, noticing it's been changed, overwriting it.

Does anyone know what's going on here? - Is my grub possibly not on the MBR, but instead in hda1, and somehow is just getting targetted by whatever is in the MBR?

I'm not really that clued up on what exactly happens in the boot sequence, so if there's something in here that's blatantly incorrect or just makes no sense then that's probably the problem.

Thanks for all help.
Simon

---

### Post by manicka on 2006-02-05
You should be able to set which drive the mbr is on during the grub restore procedure you have already followed. 

I've also found this page contains helpful information for setting up dual boots

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Isfria on 2006-02-05
Thanks, I found my problem (not a solution, just the problem).

For some really odd reason, my XP install (hda2) has it's bootloader installed on hdb1 (my downloads/music/games NTFS drive). 

The location for the XP install I have verified both in windows and linux, but GRUB autodetects XP on (hd1,0). If I try to change the GRUB entry for XP to (hd0,1) then it says it can't find NTLDR.

When I run the (hd1,0) XP GRUB entry, it just writes the entry to the screen then locks up. After that, rebooting just automatically loads the windows bootloader.

I'm just gonna check my bios options, then I'll edit this with more info.

---

