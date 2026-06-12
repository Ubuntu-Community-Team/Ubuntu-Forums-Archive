---
title: "Toshiba vs HP for Linux?"
date: 2011-09-29
forum: Hardware
---

### Post by ajukilibodin on 2011-09-29
Hello,

So, I am to buy a new laptop. Either a HP Pavilion g6-1151/1153/1150 (same thing really, color changes only) or a Toshiba Satellite C660-20L.

And of course, I'll be running Ubuntu in it. Toshiba has an Atheros card in it, while HP is Base-T or something odd like that. Anyone had any issue, problems with any of these brands? I'll be using them for school, so nothing fancy needed. Yet I want to be able to run aircrack-ng, so need a packet injectable card.

Another issue is durability, my Fujitsu laptops plastic is all broken, so I need something that will be more durable. Gonna use it for 2 years only. But it should be able to support, say 48h uptime or so.

So anyone who used these brand laptops before, which one should I get?

---

### Post by CatKiller on 2011-09-30
I've not researched either brand myself, but my mum has had one of each. The Toshiba was horrible; nasty and cheap. The HP had much better build quality, but the partitioning scheme was designed entirely to annoy people that want to dual-boot. Didn't have hardware compatibility problems with either of them, though.

Avoid anything that uses Optimus.

---

### Post by mörgæs on 2011-09-30
Have you read the sticky threads?

---

### Post by sanderd17 on 2011-09-30
I had a tochiba with quite a lot of hardware problems, and I also met some people with toshibas who had difficulties running Linux. More problems with Toshiba than with most other brands.

In general, HP, Dell and Acer work very well.

---

### Post by SeijiSensei on 2011-09-30
I installed Kubuntu 10.10 on my daughter's new HP dv6tse a few months back.  I liked the machine quite a bit, but CatKiller's comment about partitioning is spot on.  HP drives come with all four primary partitions in use; none of them is an extended partition.  If you go the HP route, here's what I'd recommend.  You'll need a USB drive or a network share to create the backups described below.

1)  Boot from the Ubuntu disk, then open a terminal and use dd to create an image of the first partition onto the backup device.  That holds the Win7 replacement disks.  If you use a USB drive, the command would be:

```
dd if=/dev/sda1 of=/media/disk/win7.img
```

assuming the USB drive is mounted as /media/disk.

You can only make one set of the Windows disks, so making a copy of the partition first will get around this limitation.  If you ever need another set of disks, you can restore the original partition from the image with dd.

2)  Now boot Windows and use HP's utility to make yourself a set of Win7 DVDs.  

3)  Boot again from the Ubuntu CD.  Use "fdisk -l" to list all the partitions; you'll need that in a moment.

4)  Use dd to make an image of the fourth partition (/dev/sda4); we'll be restoring it again soon.

5)  Use fdisk to delete partitions 3 and 4, then create a single extended partition that uses all the unallocated space.

6)  Use fdisk to create a new logical partition in the extended area to hold Windows and mark it as NTFS.  Make sure you leave enough unallocated space to hold Linux and any files you might put there.  My daughter's machine had a 640 GB drive; I think I allocated about 100 GB to Linux.  

7)  Use fdisk to create a new logical partition in the extended area that has the same number of cylinders as the old partition four did.  Then use dd to copy back the image of that partition you created in step four.  (I think this one should also be marked for NTFS, but I can't remember for sure, and the computer is now hundreds of miles away at college.)

8)  Use fdisk to create a new logical partition in the remaining unallocated space into which Linux will be installed.  Mark it for Linux.  

9)  Re-install Win7 into the NTFS partition you created in step six using the disks you made in step two.  You'll be pleased to discover this version of Win7 has a lot less additional crap compared to the factory installation.

10)  Install Ubuntu into the Linux partition created in step eight.

If you buy a machine with an ATI Mobile Radeon as we did, you may need to upgrade the BIOS as I describe [here]("http://ubuntuforums.org/showpost.php?p=11244073&postcount=2").

I don't recall which wifi adapter this machine had, but it was recognized by Ubuntu during installation.

---

### Post by mörgæs on 2011-09-30
That was quite a manual, thanks. Does this apply to all newer HP's? 

If you have the time, it would be great if you could post your experiences in 
[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

---

### Post by pwabrahams on 2012-10-03
My new Lenovo has the same problem: four primary partitions initially in use.  I wish they didn't do that -- and of course, Lenovo isn't likely to be helpful with any workaround.  It would have been so easy for them to use an extended partition.

---

