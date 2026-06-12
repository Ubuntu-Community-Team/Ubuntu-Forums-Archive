---
title: "Encrypted 9.04 on external USB drive not booting"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by shaunconn on 2009-07-06
Hi

I'm trying to install 9.04 using the encrypted LVM option (guided).  It partitions and installs correctly into 3 partitions (1 - encrypted boot, 2 - swap, 3 - unencrypted).  No matter where I choose to install grub I get "boot sector not found".

Im assuming grub needs to go on the 3rd partition as my BIOS can't see anything on the first one at boot time (as it's encrypted), however, the installer only seems to mark the 1st one as bootable.

I have tried editing menu.lst before the install finishes to point to the correct groot, but im not sure this is helping.

Has anyone installed *encrypted* 9.04 on an external drive?

TIA

Shaun

---

### Post by Herman on 2009-07-06
I haven't tried installing to a USB drive with an encrypted file system yet, only in an internal hard drive, but I do think it's a great idea! :)
All laptops and USB external drives should be encrypted, and maybe some desktop computer hard drives too.
I was planning on trying out a USB flash memory stick encrypted installation sometime soon. 

I think it would make sense to install GRUB to the USB drive's MBR and optionally also to the first sector of the /boot partition, just for good measure.

---

### Post by shaunconn on 2009-07-06
Hi

I've tried that - I've tried to install grub on my external drive in partitions /dev/sdb1 (the encrypted one) or /dev/sdb5 (the unencrypted one), but when the laptop boots it either doesn't see /dev/sdb1 grub (as its encrypted) or doesn't see the boot sector.

I seem to recall having to edit groot in the menu.lst, but just wanted a copy of anyone's who has this working!

Regards
Shaun

---

### Post by Herman on 2009-07-06
The MBR in your case would be /dev/sdb in Linux terms, or (hd1) in GRUB terms, if your partitions are /dev/sdb-something.

If you're booting from your BIOS it would be important to have GRUB installed to the USB's MBR. If you're chainloading from another boot loader (in your first hard disk maybe, or from a CD or floppy disc etc, then you can have GRUB installed in a partition boot sector. :)

---

