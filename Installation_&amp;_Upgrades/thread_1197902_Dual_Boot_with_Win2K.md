---
title: "Dual Boot with Win2K"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by Bini_1 on 2009-06-26
So the question is, how easy is it to install Win2K on a machine with Ubuntu and get it dual booting.

I know it should be straight forward doing it the other way round - but when I tried it that way the NTFS and swap partitions got utterly munged.

So now I have a working Ubuntu (using a swap file)  and a couple of knackered partitions.
If I recreate the partitions and install Win2K, can I expect Ubuntu to work still ?
Has anyone done the installs that way round ?

Bini

---

### Post by merlinus on 2009-06-26
Yes, but you better know exactly what you are doing.  Check out dual-boot guides, especially the ones at

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Best to install win2000 in the first partition, but as long as it is a primary, you will be okay.  It needs only one partition, whereas linux uses at least two, one for / (root) and one for /swap.

You will have to restore grub afterwards, but that is very easy.

---

### Post by revlarry on 2009-06-26
I have two computers with both Ubuntu and Win2K on them.

The first response, suggesting that you install Windows first, was how I did this on my first machine. It works well, and I have had no conflicts or problems across the drive. 

Last week, I installed Ubuntu 9.04 on a new machine, then added VirtualBox, and then loaded Windows 2K into the VirtualBox. All seemed quite easy and it worked well the first time. I have installed my needed Windows ap there, and it too works well.

One last idea, tried on a 3rd machine, was to install Ubuntu and then add WINE. My ap seems to work well under WINE. 

I am far from an expert, but I know this is possible. Good luck!

---

### Post by presence1960 on 2009-06-26
It is fairly straightforward to add Windows to any primary partition after Ubuntu is already installed. Create a new partition for Windows if you haven't done so already with the Ubuntu Live CD using Partition Editor or gparted Live CD. I am not sure if 2000 uses NTFS or FAT32, but create a partition with correct filesystem. Once you have created a primary partition for your windows install, boot the Windows install CD and install windows to that partition.

When you are done the installation you will have to restore GRUB.

here is a link to a thread where others were claiming you can't install windows after ubuntu, but it was successfully accomplished. it is really no harder than installing Ubuntu after windows, just that you have to restore GRUB which is so simple a caveman can do it.

[http://ubuntuforums.org/showthread.php?t=1191763](http://ubuntuforums.org/showthread.php?t=1191763)

[http://ubuntuforums.org/showthread.php?t=1193997](http://ubuntuforums.org/showthread.php?t=1193997)

---

