---
title: "grub + SATA RAID not playing nice..."
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by Antiparadigm on 2005-11-26
Hey all,

I'm having a problem with my SATA RAID array.  On my computer I have 3 HDs.  2 are SATA RAIDs using a SIL 3112 chip.  So this is a software raid.  These house my Windows XP partion on a RAID 0 (Stripped) array.

*Unfortunatly, I need windows for the Macromedia software for my bro.  Yes, I know about Crossover Office, and in fact, I really like it and have the needed software working in it on another computer.  The problem is, he claims that he can't figure anything out and needed it installed in a rush, hence on my computer.*

Back to the problem.  The 3rd drive is an IDE 80 GB that has Ubuntu on it.  Both OSes are Pretty much fresh (esp. Ubuntu) and updated.

The problem I'm having is Ubuntu can't seem to find my ntfs partion on my SATA RAID.  I've edited my menu.lst, ran mdadm, but nothing seems to work.

Here is some info:
Here is my current menu.lst:
[http://www.antiparadigm.net/menu.lst.orig.txt]("http://www.antiparadigm.net/menu.lst.orig.txt")

I ran this command to try and inform linux of the array (which didn't do the trick):
[FONT="Courier New"]sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sda /dev/sdb[/FONT]

If anyone has any info on how to get Grub to work or if it is impossible and I need to redo my hard drives, any help would be appreciated.

Thank you

---

### Post by Antiparadigm on 2005-11-26
Thanks for reading the post, but due to another prob on a different computer, I need to play hard drive shuffle, and lose my IDE drive.  I will just run my 2 sata drives in non raid mode.

Sorry for the post.

---

