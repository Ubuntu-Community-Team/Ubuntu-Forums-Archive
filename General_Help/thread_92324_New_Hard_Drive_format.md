---
title: "New Hard Drive format"
date: 2005-11-19
forum: General Help
---

### Post by johnfarrow on 2005-11-19
Hello all,
   I have a Thinkpad (T23) and I am going to install a new 80 gig drive that I intend to install XP Pro (from an exsisting drive) and Ubuntu so I can dual boot.

Is there any problems formating the new drive as NTFS?
Should the new drive have equal partitions? (half for xp and half for Ubuntu)

Any thing else I should be concerned with before starting this project?

Thanks

John

---

### Post by taurus on 2005-11-19
Install XP first and make sure you leave an empty partition (doesn't have to be in equal size) to install Ubuntu later.  Once you are done with XP, boot Ubuntu CD and tell it to use the empty partition.  Then, create at least two more partitions from that empty partition, / & swap (or you can create three more for /, /boot, & swap).  Then, sit back and enjoy the show.  Should take probably about half an hour at which stage it will ask you to remove the CD and reboot.  After rebooting, it will continue with the installing and you are pretty much done.

p.s.  Grub, Linux bootloader, should be able to boot your XP as well so no need to worry about that.

---

### Post by metoo on 2005-11-19
Writing to a NTFS partition is not well supported in Linux. It seems to work with some wrapper, using original libraries, but by default this partition will be read only. It's not that easy to get it going. You may want to read about this first (here in the forum or in the wiki).

If you want to write from the Linux partition to the XP one, better use FAT32 if you can. The xp installer has a size limit up to which it is offering this format.
(You might be able to format the xp partition from a linux live CD using cfdisk).
With FAT32 you have the 4GB per file size limit as a disadvantage.

---

### Post by essexman on 2005-11-19
If the xp is not registered to that machine, avoid connecting the xp installation to the internet as it could stop working.:(

Very clever, those microsoft peopleO:)

---

### Post by bonzodog on 2005-11-19
incidentally, when you create Ubuntu create 3 partitions; a swap, /, and /home. You don't need a /boot partition. Dont let the partition manger auto create them as it will only give you a / and swap. Having a /home is useful as you can use it to permanently store your data on, and you should never need to remove it. Just remember that XP won't see it.

---

