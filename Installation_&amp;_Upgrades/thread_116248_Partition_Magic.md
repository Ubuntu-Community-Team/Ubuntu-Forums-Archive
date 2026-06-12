---
title: "Partition Magic?"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by Painter on 2006-01-12
Hi,
 Has anyone here used Partition Magic to create a Linux friendly partition? There are several choices Fat, Fat32, Linux ext2, Linux ext3 and Linux swap.... spoiled for choice! Which one should I use, or would'nt you recommend using PM to do it? I'm terrified of doing something irreversible. I've got all my data safely on DVD's....
Cheers,
F

---

### Post by DoorGunner on 2006-01-12
Please note that ubuntu can actually do the install on its own as well. you just have to tell it how much space it can have.

However, I used partition magic for my installation. Actually what i did was create some freespace on the disk and then let Ubuntu install the file system to that freespace......

You will need to do a bit of planning. How much room do you want to give to ubuntu? Do you want to have a share file for windows and ubuntu?

That way there is no mistakes. Ubuntu is fairly easy to install.

Prior to any install you should defrag your hard drive.
-----------------------------------------------------------------------
Partitioning
mine for all intensive purposes looked like this. ( i actually have fedora, ubuntu and gentoo on my machine)
fat32 5Gb > ntfs 195Gb

i then created freespace that looked like this
fat 32 5Gb > ntfs 95Gb > Freespace 100Gb

I installed Ubuntu to that freespace and it now looks like this
fat32 5Gb > ntfs 95Gb > Ubuntu 100Gb

Note: ubuntu will actually be in 3 partitions but it does it itself
All you have to do is select install to freespace when you come to that.
If you want a share file....add in a fat32 file for your mp3s movies etc to share between windows and linux

------------------------------------------------------------------------

here is a site you can look at for the install
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2)

when you come to the partition if it recognizes that you have freespace it will ask you if you want to install it there....say yes to that option or if it isnt there then use the manual partition to place it in your freespace.

---

### Post by Painter on 2006-01-12
Thanks!
That makes life a bit simpler.I'll give it a shot.
F

---

### Post by Begatelles on 2006-01-12
Yes, good idea for a Fat32...especialy if you are migrating from Windows and still use them. Another thing, it would be best to install Ubuntu on more than one partitions. For example create another /home partition along with your /root. That way if anything goes wrong and system crashes nothing happens to your work. Later you can keep adding more partitions to customize it to your needs.

---

### Post by aysiu on 2006-01-12
Even though it's targeted specifically at setting up a dual boot from scratch, the fifth link of my sig is a good walkthrough on using Ubuntu's own native partitioning tool during the installation process (it has screenshots, too).

Otherwise, I would also recommend [using DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

---

### Post by Painter on 2006-01-12
Great stuff,
I obviously have a lot of homework to do! There are times when at my age, looking at yet another incomprehensible windows error message i find myself quoting Danny Glover....Getting too old for this s**t... It really helps to find people willing to help out. 
Thanks all.
F

---

