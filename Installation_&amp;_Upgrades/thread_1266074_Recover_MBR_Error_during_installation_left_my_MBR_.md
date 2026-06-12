---
title: "Recover MBR: Error during installation left my MBR DOA"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2009-09-14
Ubuntu 9.04

Greetings, family.

I was trying to reinstall Ubuntu (due to an unclever action on my part that messed it up) and am in the process of reinstalling it with a new partition setup. In the new setup, my XP partition is to remain where it is (as before), followed by the 4GB swap partition and that is followed by a 84GB root partition.  (Dinosaur BIOS - max 4 partitions, all beginning before 128GB.  Old story.)  I would be sceptical of an suggestion that this is part part of the problem.

The installation was humming along until it hit 73%, whereupon it encountered an error and just died there.  When I tried to boot XP thereafter, I got this error message:

> 
GRUB loading stage 1.5
Grub loading, please wait

Error 17


No boot menu.  (I am booted on the Ubuntu  CD now.)

Aside from the fact that my master boot records is obviously hosed, can anyone tell me exactly the meaning of this error message?  And where would I find this (besides asking like this)?

I plan to dig up the XP installation disk now to use the recover console and the fixmbr command.  I suspect I need to burn a fresh copy of ubuntu. I download a fresh copy of the 9.04 .iso file yesterday.

This, after a similar installation debacle last year?  Man, this guy just won't learn a lesson!

Thanks much!

-- Rasputin Paskudniak

---

### Post by Partyboi2 on 2009-09-14
Make sure to check the cd for defects (one of the options at the main menu of the live cd) 
You can read about grub error 17 [[COLOR=Blue]here[/COLOR]]("http://members.iinet.net.au/%7Eherman546/p15.html#17"). But this could be caused since the installation did not complete.
What error message did you get?

---

### Post by rpaskudniak on 2009-09-14
Partiboi (Cute moniker :)  )

A bit of confusion ensues, although the link you provided was packed with [scary] information.  For the benefit of other reading this thread, I will quote the passage:

**When trying to boot Windows** having the NTFS file system (even if you only have one hard disk) 
GRUB error 17 can be caused by using the 'root' command instead of 'rootnoverify'
It is a little better to use 'root' if you have the FAT32 filesystem, but use 'rootnoverify' for NTFS.
Edit your commands in your _menu.lst_ or _grub.conf_ file with 'rootnoverify' to get rid of this error message.
For example,
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root[COLOR="Red"]noverify[/COLOR]        (hd0,0)
savedefault
makeactive
chainloader    +1

(I have tried to replicate the passage formatting.)

OK, since I can't boot Windows or Ubuntu and can only boot from this Ubuntu installation CD, where do I find these two files? Presumably someplace where the Windows boot process will be able to find them. Is my problem NOT in the MBR after all?

Thanks much!:popcorn:

---

### Post by rpaskudniak on 2009-09-14
[FONT="Arial Black"][SIZE="2"]Solved[/SIZE][/FONT], without the scary messages from the XP recovery console!

During my last year's disaster, I downloaded and burned the SuperGrub Disk, release 0.9677. For the benefit of the unfamiliar, I got it from [_[COLOR="Blue"]here[/COLOR]_]("http://www.supergrubdisk.org/"). It is up to release 0.9798, to be replaced by a version based on grub2.

What I did:
I booted from the Supergrub CD and actually looked at the extensive menu. The last item reads something like:
> Windows + MBR
I picked that one and it started to boot windows like nothing was wrong.  One quirk:  It requested I reboot again because "Windows had detected new hardware".  (I had installed a new printer since last year and, to my best guess, this is the new hardware.)  I popped the SG CD and allowed the reboot.

No problem!  YEAH!! :guitar:

As to this grub2 business: The web site is a bit confusing but I am about to download the latest grub[1] version from their [[COLOR="Blue"]_mirror site_[/COLOR]]("http://prdownload.berlios.de/supergrub/sgd_cdrom_1.21.iso.gz").

Get it!

Thanks, all (and especially partiboi) for being my sounding board so I could hear the solution.

---

