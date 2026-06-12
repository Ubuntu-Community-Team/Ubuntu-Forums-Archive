---
title: "Drive Partitioning Debacle"
date: 2005-11-19
forum: General Help
---

### Post by fontosaurus on 2005-11-19
So I ordered a brand-new Dell laptop, specifically to run Ubuntu. I decided to keep a 10 gig WinXP partition for running Civ3/Civ4 on. I've booted off the LiveCD for Ubuntu 5.10, but in using Gparted, I cannot seem to get a partition going.

On startup, GParted reports the following partitions:

/dev/sda1     
fat16      
size: 39MB
used: 32MB
unused: 7MB

/dev/sda2
ntfs
size: 51199 MB
used: 7816 MB
unused: 43383
FLAG: boot

/dev/sda3
fat32
size: 4754MB
used: 4049MB
unused: 705MB

Unallocated (previously reported as /dev/sda4)
previously reported as something, but I can't remember what
size: 8MB
used: ---
unused: ---

Prior to this, I was getting errors regarding not having more than four logical partitions.  

What I'm trying to do is get the Windows partition down to 10000 MB and give the remaining 41199 MB to Ubuntu. 

Can someone walk me through this?  (I'm a Mac OS X geek, so I don't normally futz with Wintel hardware, nor things like drive partitioning.)

---

### Post by campusloop on 2005-11-19
Does the partitioner offer any other choices besides "erase entire disk".

a hard drive cannot have more than 4 primary partitions and you already have 3 primary partitions ( even after you resize your windows partition ) like 
/dev/sda1, /dev/sda2 resized to 10GB and /dev/sda3. 

and you will need two more partitions to install linux - one for swap and another for root so the trick here is to create two logical partitions to overcome the 4 primary partition limit. you can do this by selecting "manually  edit partition table". 

I have never resized partitions so i am not sure how to that from within ubuntu installer.

---

### Post by Irony on 2005-11-19
Assuming you have XP on the laptop and you now want to install ubuntu for a dual boot system, then you can shrink your windows (ntfs) partition during the ubuntu install. See;

[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html) (Hoary 5.04)

and for more detail see;

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) (Breezy 5.10)

In other words after you have backed up your data and defragged your windows drive, boot up from the ubuntu install disc and follow the above links for how to shrink your windows partition.

What you do is to create free space for the ubuntu installation. You can then install to this free space either automatically partitioning into swap and ext3, or you can select their sizes.

In fact you can go back and forth at this point to create free space and then divide up the free space into extra partitions (of any type, which you can then format with gparted once the install is finished).

When it comes to installing the GRUB bootloader install it to the MBR and it will detect the windows partition for a dual boot (no configuring necessary.)

You also want to plan what partitions you want. You can have 4 primary partitions, or 3 primary partitions and one extended partition. Within the extended partition you can have as many logical partitions as you like.

You might want to have hda1 as primary, hda2 as ext3 (ubuntu), hda4 as ext (swap) and hda4 as primary. hda4 can be turned into logical partitions later.

---

