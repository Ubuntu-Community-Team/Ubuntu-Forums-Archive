---
title: "Using gparted to delete Ubuntu 8.04"
date: 2008-11-14
forum: General Help
---

### Post by blindscout on 2008-11-14
I had ubuntu 8.04 on one part of my disk and win xp on the rest. then when 8.10 came out I installed it as well, thinking it would replace/update the 8.04. even when the partition manager came up I only saw my win xp sp2 partition and the new one (8.10) so i figured it had already deleted it.

it didnt though so now whenever i boot my pc there are 3 choices to boot up from there. thing is i want to remove 8.04 and give the space to win xp. and have only that and 8.10.

I have been told that the correct way to do that is with GPARTED. so i ran gparted live cd but the thing is i do not know what partitions to delete because i do not know what the dev/sda1 and what not mean..
there are a couple of those there.

This is what I see in gparted.

/dev/sda1 - file system:ntfs - size:125.82GiB - Used: 68.03 - Unused:57.69 - Flags: boot

/dev/sda2 - file system:extended - size:107.05GiB - Used: --- - Unused:--- - Flags: lba

/dev/sda8 - file system:ext3 - size:29.29GiB - Used: 2.64 - Unused:26.65 - Flags: empty

/dev/sda9 - file system:linux-swap - size:1.30GiB - Used: --- - Unused:--- - Flags: empty

/dev/sda6 - file system:ext3 - size:37.25GiB - Used: 2.79 - Unused:34.46 - Flags: empty

/dev/sda7 - file system:linux-swap - size:1.64GiB - Used: --- - Unused:--- - Flags: empty

/dev/sda5 - file system:ntfs - size:37.57GiB - Used: 28.56 - Unused:9.01 - Flags: empty

unallocated - file system:unallocated - size:7.84MiB - Used: --- - Unused:--- - Flags: empty


What should I delete from all this in order to keep windows xp and ubuntu 8.10 and give the space freed to windows xp ?


Say I've figured out which one is the ubuntu 8.04, do I delete the ext3 AND the linux-swap below it? or just the ext3 and the swap goes with it?


Thanks a bunch!

---

### Post by louieb on 2008-11-14
Boot Ubuntu and run the **mount **command.  or install Gparted it will also list what is mounted where.  As a general rule if it mounted in /media the partition is not needed by Ubuntu. 

Just looking at it. adding the unused space to XP is not going to be easy. The unused space has to be next to the partition you want to add it to. 
also the unused space will be inside the extended partition.  

You really should know about the 3 types of partitions before you begin primary, extended and logical.  [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by blindscout on 2008-11-14
I just want to have windows xp and the latest linux 8.10. :P

---

### Post by blindscout on 2008-11-15
Well I figured out which distribution is which.
8.10 is dev/sda8 and 8.04 is dev/sda6 ;p

Now I'm almost certain I should remove this

/dev/sda6 - file system:ext3 - size:37.25GiB - Used: 2.79 - Unused:34.46 - Flags: empty

But I don't know what else...

Any help ?

---

### Post by louieb on 2008-11-15
The safest thing to do is to format the partition with the NTFS file system. Then it will show up in windows as another drive you can use for data storage.

---

