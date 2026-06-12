---
title: "Dule Boot Ubuntu With Windows XP"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by DJeX on 2006-01-30
I want to be able to duel boot ubuntu and windows xp but unbuntu and xp are on separate hard drives. 

I need a way that will not wreck my Windows XP NTFS partition table as like what happened to me the last time I installed ubuntu (too me 3 days to fix).

My XP hard drive is the master and ubuntu will be on a slave. So basically I need a different way to duel boot ubuntu and xp with out totally screwing my other hard drives up.

*All other hard drives are NTFS except linux hard drive which is FAT32.

---

### Post by C J Pro on 2006-01-30
I think you can just tell it to overwrite your slave drive without worrying.  I put Windows as the slave on my computer though and it worked perfectly for me.  Better yet, if I ever screw up Linux, I just have to swap drives and I can access Windows again.

---

### Post by ta6ape on 2006-01-30
Before you install Ubuntu make sure to have the secondary(Linux) hard disk to boot before the primary(Windows), through your computer's BIOS. Then install Ubuntu and make it install GRUB on the secondary drive (as you want). 
This way you won't touch the Windows installation and the MBR will have the default windows loader and not GRUB.
When you want to just boot windows, adjust the BIOS to boot the primary(windows) disk! Do the opposite to boot Ubuntu!
I tested this and it works well!

---

### Post by DJeX on 2006-01-30
How do I make it install GRUB on the secondary drive?

---

### Post by DaBruGo on 2006-01-30
Hi folks,

I don't know if this helps you all out, but I started a thread relating to this dual boot issue a little while back.

I have XP loaded on my internal drive and Ubuntu loaded on an external usb drive. And, I can boot either from the GRUB menu.

The thread is titled ...
[SUCCESS - Breezy loaded on external USB drive !]("http://ubuntuforums.org/showthread.php?t=80811")


Hope that helps,
DAVE

---

