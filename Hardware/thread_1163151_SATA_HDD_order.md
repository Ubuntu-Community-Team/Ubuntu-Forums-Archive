---
title: "SATA HDD order"
date: 2009-05-18
forum: Hardware
---

### Post by KamikazeNY on 2009-05-18
Hey everyone. I've searched around but I'm a little confused how Linux does things with regards to multiple sata discs.

Originally I had 2 identical discs that I configured with software RAID-1. Ubuntu recognized these as /dev/sda and /dev/sdb. These discs were connected to my mobo as SATA 1 and SATA 2. 

I added a third identical disc to the SATA 3 port but when I booted up I saw that my third disc was now /dev/sdb and one of the mirrored discs was /dev/sdc. A quick look at mdadm confirmed that the RAID-1 array was using to sda and sdc.

My question is how does Linux determine the order that devices appear in /dev (i assumed the channel order would be preserved) and also, what level of intelligence is there regarding the mounting process? Obviously something 'smart' happened because it realized one of the discs in my array was now sdc and not sdb, and booted up just fine. How and where is this configuration maintained? In fstab? In grub? And lastly, how does Linux identify drives? Is it just by their /dev or does it read the drive S/N or something?

Sorry for the long winded question, but this is the first time I've been genuinely confused over a Linux concept. :)

Thanks!

---

### Post by logos34 on 2009-05-18
I believe the 'musical sata drives' issue is caused by the order in which the sata controllers (you have two I'm guessing) and the disks that are connected to them are initialized and recognized by the Bios...But, happily, drive letters don't matter anymore as ubuntu distinguishes disk partitions by UUID #'s.  The UUID is what counts.

Look in /etc/fstab 

or run this in terminal to see the 'kernel' line in /boot/grub/menu.lst:

cat /proc/cmdline

(--> / partition)

sudo blkid 

lists all the partitions uuids

Everything will boot and work normally, but I agree it can be confusing when 

sudo fdisk -l

is different every time

---

### Post by KamikazeNY on 2009-05-18
Ahhh, it all makes sense now. Appreciate you clearing that up. :)

Cheers!

---

