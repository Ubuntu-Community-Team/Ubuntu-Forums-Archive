---
title: "Installing with raid?"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by DannyW on 2007-05-04
Hello,

I'm hoping for some advice for setting up raid. I've recently ordered components for a new computer.

I've ordered an Asus P5b Deluxe and Core 2 Duo E6320.

The storage specification for this motherboard says:
> Southbridge
 - 6 x SATA 3.0 Gb/s ports
 - Intel Matrix Storage Technology supports  RAID 0, 1, 5 and 10.
JMicron® JMB363 PATA and SATA controller
 - 1 x UltraDMA 133/100/66 for up to 2 PATA devices
 - 1 x Internal SATA 3.0 Gb/s port
 - 1 x External SATA 3.0 Gb/s port (SATA On-the-Go)
 - Support SATA RAID 0, 1 and JBOD (by 1x External SATA & 1x Internal SATA)

I've got two roughly 250GB sata drives and have just ordered 2 500GB sata drives.

I have zero experience with raid. Is it possible to use the two 250GB drives in a raid 0 array and then use this raid 0 array in a raid 5 array with the two new 500GB drives?

I also have a 350GB IDE drive which I'm assuming can take no part in this?

Would I use the Intel controller or the Jmicron controller? Or neither?

I'm open to suggestions for better ways of achieving this.


I would like to have the option of using this array in windows also, however, I will be using Kubuntu primarily.


Please do not hesitate to provide any advice at all, or even links to pages which may explain solutions to a similar problem.

Thanks,
Danny.

---

### Post by ohgod on 2007-05-04
I don't know the answers to most of your questions, but if you want a raid 5 setup you need 3 drives that are the same size (or you could use 2-250gb drives and 1-500gb, but you would be wasting space on the 500gb one...better to have 3 identical drives).  I don't think there's much of a reason to make a raid 1 array then use it in a raid 5 array.

You might want to check the hardware compatibility lists to see if the raid controllers are listed there.

Here's a good description of raid levels that I reference occasionally:
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by DannyW on 2007-05-05
> **ohgod said:**
> I don't know the answers to most of your questions, but if you want a raid 5 setup you need 3 drives that are the same size (or you could use 2-250gb drives and 1-500gb, but you would be wasting space on the 500gb one...better to have 3 identical drives).  I don't think there's much of a reason to make a raid 1 array then use it in a raid 5 array.

You might want to check the hardware compatibility lists to see if the raid controllers are listed there.

Here's a good description of raid levels that I reference occasionally:
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

I apologise, I meant raid 0, so my two 250GB drives would then be aprrox 500GB, giving me 3x500GB drives.

Thanks for the wikipedia link also.


I've been doing some looking around, it seems fakeraid is not the preferred way to do things. I've been reading several pages about software raid (mdadm) and LVM.

Although I would still like any information on this, I have another question: would it be possible to browse a linux software raid array on windows, I recall reading of a program which allowed browsing of LVM LV's.

Also, does anyone know of an up to date howto on how to install LVM on software raid.

Thanks again.

---

### Post by gerscht on 2007-05-07
> **DannyW said:**
> I apologise, I meant raid 0, so my two 250GB drives would then be aprrox 500GB, giving me 3x500GB drives.

I'd do a RAID6 with 6*250GB partitions (not using the whole drives of the 500gig ones, but 2*250GB partitions on them)
Your net capacity would be around 1TB, and it would be failsafe if one 500gig (as it contains two nodes of the array) or both 250gig disks go down.

You wouldn't loose any space compared to your idea, but I think it would be less complicated :)

---

### Post by zero-Q on 2007-05-07
I am using edgy on raid0. but there is aproblem with feisty and raid. could u tell me what you see in next boot after livecd boot in bios raid screen. my raid hdd apear as offline whenever I boot from livecd at next reboot. and on the other If I try to use dmraid, I ll get this error message:"root@ubuntu:~# dmraid -ay
ERROR: isw device for volume "Volume0" broken on /dev/sda in RAID set "isw_cgffbhhfed_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_cgffbhhfed_Volume0" [1/2] on /dev/sda" please could u share ur experiance with raid and feisty?

and to install edgy on raid0 I suggest [this guide]("http://www.howtoforge.com/ubuntu_dapper_raid_system") but u have to make some changes on the guide like the places called "dapper" to "edgy". and if u need help u can ask me anything about raid&edgy...

---

### Post by Tilo on 2007-05-31
I would not use two physical 250GB drives to make one virtual 500GB , which is part of another raid  - sounds like bad carma to me.

I would recommend:
 - put your boot/root partitions on a non-RAID volume (so you don't suffer from slooooow booting
   when your RAID is being repaired)
 - put your data on a RAID6 volume, or if you don't have enough drives, on a RAID5 volume

so if you're not flexible with getting other drives (try to make all members of a RAID the same type
and size of drive),   then make partitions on each of your drives which have the same size , and use them to create a RAID5 or RAID6 - in your case, use 250GB partitions, and use the remaining free space on the 500GB drives to put your root/boot partitions on - don't put two RAID members on the same physical drive - bad carma if a physical drive fails...

---

