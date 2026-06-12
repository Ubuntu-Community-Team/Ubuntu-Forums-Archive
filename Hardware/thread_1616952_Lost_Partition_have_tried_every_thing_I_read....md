---
title: "Lost Partition have tried every thing I read..."
date: 2010-11-08
forum: Hardware
---

### Post by lvlouro on 2010-11-08
I have a HDD that's in ext2, it's an external HDD although I've removed it from it's case just to make sure the usb wasn't causing anything weird.

Main thing, I've used testdisk and it detects the correct partition I can even see the files there, therefore I use the write option and reboot...

But it doesn't work and the weird thing is that when I launch testdisk agaig it displays the same partition twice...

I really really need help have been going for several days read every forum I could find and can't find an answer...

---

### Post by lvlouro on 2010-11-09
Just to add a few things...
 
gparted gives an error I can't recall right now and doesn't initialize
 
gpart only finds a swap partition that's 1TB (that's not found in testdisk) that I believe is my ext2 partition since I only have one partition in the disk...

---

### Post by srs5694 on 2010-11-09
First, try running a SMART test on the drive. If you're writing to the drive but those writes aren't "taking," it's possible that your drive has enough bad sectors that it can't remap a bad sector in a *very* bad place (namely, sector 0, where the MBR partition table lives). If the SMART status is bad, your best bet may be to do a sector-level copy of the disk to another disk and try again on it.

Second, if you can get TestDisk to report the *exact* sector values of the start and stop of the partitions it finds, you can reproduce the partition table in fdisk and write it that way. (Launch fdisk by typing "sudo fdisk -u /dev/sdb", or whatever the disk filename is; the "-u" option is critical to get sector numbering.) This approach should work if your drive is OK but TestDisk isn't writing to the disk for some unknown (but TestDisk-specific) reason. I'm not that familiar with TestDisk, so I can't give you advice on getting it to report sector-precise partition start and end points.

Third, if you've got failing hardware, it's conceivable you'd have better luck with another partition table type. IIRC, the Apple Partition Map (APM), used on older Macs, doesn't use sector 0 for much, so you might be able to get the disk to work as an APM disk even if sector 0 is hopeless. You'd need to tell TestDisk to write an APM table rather than an MBR (MS-DOS) table. This would at least enable you to recover your data onto another disk, although you might not be able to boot Linux from the disk, if it's currently bootable. Linux supports APM just fine, but I don't know offhand if Ubuntu built for x86 or x86-64 systems includes APM support. (It's a compile-time kernel option.) OTOH, if sector 0 is hopeless, it's also possible that surrounding sectors, including sector 1 (which *is* critical to APM) are also bad, so this is far from a sure thing.

---

### Post by lvlouro on 2010-11-09
Ok, SMART status I had already checked and it's healthy

[IMG]http://img574.imageshack.us/img574/6059/testdisk.png[/IMG]
testdisk results I'm guessing start it's 0 and end 121600 but that's odd since the partition occupied the whole disk and size in sectors is 1953520002 ???

I'm a total noob in this, even so I ran fdisk as u said and when I chose the add partition I couldn't choose the 0 as start... only above 2048

---

### Post by lvlouro on 2010-11-09
ok... the start end numbers are cylinders...

---

### Post by lvlouro on 2010-11-09
Here's testdisk log:

search_part()
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/7452, s_mnt_count=0/20, s_blocks_per_group=32768, s_inodes_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 244190000
recover_EXT2: part_size 1953520000
     Linux                    0   1  1 121600 254 61 1953520000 [Router]
     EXT2 Backup superblock, 1000 GB / 931 GiB
Search for partition aborted
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * Linux                    0   1  1 121600 254 63 1953520002 [Router]
     EXT2 Backup superblock, 1000 GB / 931 GiB

interface_write()
 1 * Linux                    0   1  1 121600 254 63 1953520002 [Router]
write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition
Need to fix
 1 * Linux                    0   1  1 121600 254 63 1953520002 [Router]
     EXT2 Backup superblock, 1000 GB / 931 GiB
You will have to reboot for the change to take effect.

TestDisk exited normally.

---

### Post by lvlouro on 2010-11-09
gparted error
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...

---

### Post by lvlouro on 2010-11-09
SOLVED :)

when posting the details for you to see I read somewhere in there the word "superblock" so I started researching it and found another thread that told how to recover using superblocks, since testdisk gave me the backup superblocks I used this command
sudo fsck -b 32768 /dev/sda1 
and after a *hitload of fixes it finally works :) SUPERCOOL

---

### Post by lvlouro on 2010-11-09
Thanks for the help, really if you didn't get me thinking I'd still be lost ;)

---

### Post by srs5694 on 2010-11-09
I'm glad to hear you've got it fixed. FWIW, I've done a bit of checking, and it seems that TestDisk is reporting partition start and end points in [cylinder/head/sector (CHS)](http://en.wikipedia.org/wiki/Cylinder-head-sector) values, which can be confusing. I suspect from your last message that TestDisk *did* recover the partition, but you needed to run fsck on it to recover the *filesystem* within the partition.

---

