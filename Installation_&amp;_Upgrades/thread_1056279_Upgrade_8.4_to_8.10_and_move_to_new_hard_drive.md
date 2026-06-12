---
title: "Upgrade 8.4 to 8.10 and move to new hard drive"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by RayDeCampo on 2009-01-31
Hello,

I currently have a SATA drive (/dev/sda) and an IDE drive (/dev/sdb).  The IDE drive has Ubuntu 8.4 installed on it with / and /boot partitions.  The SATA drive is newer, I have migrated /home to it and left about 30 GB at the front of the disk for an eventual install of 8.10.

The end goal is to have 8.10 installed on the new SATA drive, have the SATA drive contain the master boot record (which is current on the IDE drive) and not lose any of the settings/customizations I did to my original install (e.g., getting the sound card to work, installing extras like Java).  Please advise me as to the best approach.

Thanks,
Ray

---

### Post by Pumalite on 2009-01-31
Read this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by RayDeCampo on 2009-01-31
I'm not looking to dual boot, I want to migrate an existing install to a new hard drive and then upgrade.  Or vice versa, if that makes more sense.

---

### Post by RayDeCampo on 2009-02-23
Well, I got the move to a new hard drive portion done; presumably the upgrade will be as easy as using the GUI front end to apt.

To move to a new hard drive, first I already had the drive installed and partitioned in my computer.  (In fact I had moved the /home partition to it a while ago.)  I had the first partition empty and formatted with an ext3 file system but not set to mount on boot nor did it have an entry in /etc/fstab.  It shows up on nautlius however and double clicking mounted it to /media/disk.

Next I copied over my / and /boot file systems to the new drive using rsync (inspired by [http://encodable.com/tech/blog/2006/10/30/Ubuntu_Linux_Hard_Drive_Upgrade):](http://encodable.com/tech/blog/2006/10/30/Ubuntu_Linux_Hard_Drive_Upgrade):)

rsync -avx --delete / /media/disk
rsync -avx --delete /boot /media/disk/boot

Note that the -x option prevents rsync from crossing file system boundaries.

Next I knew I would have to edit /media/disk/etc/fstab to match the UUIDs of the partitions with the correct mount points.  I used /dev/disk/by-uuid to learn the UUIDs of my various partitions and made the appropriate edits.

After reading the GRUB manual online I decided the best way would be using a boot disk.  But there seemed to be no need to make a new one since my old hard drive already has GRUB installed.  I created a breadcrumb file /media/disk/boot/grub/breadcrumb so I could locate the correct partition when at the GRUB prompt.  (I was working from the directions at [http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively).)

So I rebooted, went into the GRUB prompt, installed GRUB on the new hard drive which was (hd1) according to the find command.  Next I rebooted, went into the BIOS, changed the boot order of the drives, and rebooted again.

At this point I began to encounter some issues.  When booting GRUB reported "Error 15: File not found."  I took the following steps to repair it, but I suspect not all of them were necessary.

First I thought the issue might be that changing the boot order changed my hard drive number according to GRUB.  Indeed the numbering had changed, confirmed by the find command.  So I repeated the process of installing GRUB, this time with the new hard drive as (hd0).  That did not fix the error.  I'm thinking this was unnecessary.

So I rebooted back into my old drive (fortunately by BIOS supports an ad hoc boot menu making this easy) in order to read some docs and make some changes.  I realized I neglected to change the UUIDs listed in /media/disk/boot/grub/menu.lst so I made those changes.  Rebooted, but still got error 15.  (Although I think this step was necessary.)

Googled on error 15 (after rebooting with the good drive) and found some good information at [http://ubuntuforums.org/showpost.php?p=4587202&postcount=9](http://ubuntuforums.org/showpost.php?p=4587202&postcount=9).  Unfortunately the advice wasn't quite right for me, as my hard drive number already matched.  However, it did lead to to realize that the filenames for the linux kernel image and initrd.img files were wrong for the new partition -- my old disk had a /boot partition and they were relative to that, whereas the new drive had none and they should be relative to /.  Fixed that up in the /media/disk/boot/grub/menu.lst and I was good to go.

---

