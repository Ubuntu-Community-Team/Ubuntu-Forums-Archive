---
title: "Puting an XP partition on a Ubuntu Laptop"
date: 2008-09-17
forum: General Help
---

### Post by akxiii on 2008-09-17
My friend bought a Ubuntu Dell Laptop, but now needs a program for school that will only run under XP. So I want to setup a partition for a dual boot. 

I wasn't able to find any dual boot instructions for this direction of installation. I know we aren't supposed to be pro XP on the forums ;-) but you gotta do what you gotta do.

So let me know if I gotta backup Linux and install XP over top only to install Linux over top of that.
-Thanks

---

### Post by oilchangeguy on 2008-09-17
> **akxiii said:**
> My friend bought a Ubuntu Dell Laptop, but now needs a program for school that will only run under XP. So I want to setup a partition for a dual boot. 

I wasn't able to find any dual boot instructions for this direction of installation. I know we aren't supposed to be pro XP on the forums ;-) but you gotta do what you gotta do.

So let me know if I gotta backup Linux and install XP over top only to install Linux over top of that.
-Thanks

you can use gparted or the partition manager (same thing, different name) depending on the version of ubuntu you're using. set up a partition for windows and install it. keep in mind it needs to be a legal copy of windows. and then use the live cd again to reinstall grub.

---

### Post by akxiii on 2008-09-17
Yes I have a legal copy of windows. 
How do I know how big of a partition windows needs? Like I was saying it is really just for one program. 

I have gparted up and running. Any more advice?
The partition should be FAT 32 right?

I see a boot flag on the ext3 (main) partition. Once I install windows I need that partition to be the auto boot one. So if I could get any tips with that, it would be great.

---

### Post by EmanresuusernamE on 2008-09-17
Forget the partition all together.  Install VirtualBox, and then install windows inside of the VirtualBox.  Run windows and use that program.

---

### Post by akxiii on 2008-09-17
> **EmanresuusernamE said:**
> Forget the partition all together.  Install VirtualBox, and then install windows inside of the VirtualBox.  Run windows and use that program.

sorry, need a partition. I have to have the computer be able to boot up windows

I made a live cd of GParted and popped it in. I decreased the size of the main partition, and went to create a new partition over the unallocated space. I get an error message saying that it is not possible to creat more than 4 primary partitions.

the partitions on there are as follows
partition    filesystem    Label   Size
/dev/sda1    fat16                 62MiB
/dev/sda2    fat32         OS      5GiB
/dev/sda3    ext                   92GiB
unallocated  unallocated           10GiB
/dev/sda4    extended              4.38GiB
  /dev/sda5  linux-swap            4.38GiB

The error message also tells me that I can make an extended partition, and use it as a container... ?

---

### Post by EmanresuusernamE on 2008-09-18
What's on your FAT32 and FAT16 drives?

And Windows will think it's in it's own machine with VirtualBox.  VirtualBox is like haveing a computer within a computer.  You'll be booting up a full blown version of Windows inside of VirtualBox, and windows won't be able to tell the difference.  It's different than wine.

---

