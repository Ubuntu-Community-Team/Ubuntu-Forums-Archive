---
title: "Grub won't let me into Windows"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by Curlydave on 2008-12-06
I recently redid my hard drive partitions (Bought a new drive, moved everything around). I've been set up on new Vista install for several days, with GRUB correctly working from an old Ubuntu install.

I just wiped the drive with the Ubuntu install, and installed Unbuntu on a partition on the new drive. GRUB didn't automatically set up Vista, and I can't get into it. I didn't accidentally wipe it because I can access the partition in Ubuntu and it's intact.

I've added the following to menu.lst. How do you find what code (hd#,#) your drives are? I added many labeled entries below to cover all of the bases, hd0 and 1, the second number 0-7, but it gives me varying errors when I try to load from them.

title		0
root		(hd1,0)
savedefault
makeactive
chainloader	+1


title		1
root		(hd1,1)
savedefault
makeactive
chainloader	+1

How do I fix GRUB so I can get into Vista, why didn't it work right automatically, and how do you determine your partition's code? It's easy to find the /sda#, but not the code it uses when booting. Thanks!

I've found out my hd is hd0. If the second number is above 6, the error message is "Can't find partition". If it's below 6, it's generally "invalid device". If it's 2, the message is "device not bootable, insert floppy".

---

### Post by inobe on 2008-12-06
this is how to fix grub

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

except i don't know if it would be better to fix vista's mbr first !

i don't dual boot' so i wouldn't know fore sure, assuming you want to dual boot' maybe fixing vista first ?

---

### Post by Mark Phelps on 2008-12-07
Start by running the following command in a terminal: "sudo fdisk -lu".  We can't help with specifics until we see the partition layout of your disks.

---

