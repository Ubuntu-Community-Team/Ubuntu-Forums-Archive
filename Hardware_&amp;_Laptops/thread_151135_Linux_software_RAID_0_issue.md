---
title: "Linux software RAID 0 issue?"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by tszanon on 2006-03-27
Hi, people.

I just bought 2 SATA HDDs, 80 GB each, and tried to install Ubuntu 5.10 using Linux software RAID. The installation is ok, no problems. Here are the partitions I made in each HD:

/boot - 69 MB
/ - 5 GB
/tmp - 1 GB
/var - 1GB
/usr - 5 GB
swap - 500 MB
/home - 62.4 GB (all remaining free space)

Except for /boot, I created MD devides for all other partitions. So, I have this:
/dev/sda1 - /boot
/dev/md0 - /
/dev/md1 - /tmp

and so on. /dev/sdb1 is left unused. All md's are RAID 0 and ext3 (except for swap, of course).

My problem is: when I try to handle a large file (for example, when I'm backing up the system), at some random point, everything just hangs.

It happened before, when I partitioned the disks like this:
/dev/sda:
/boot 
/dos (fat32)
/

/dev/sdb:
swap
/

/boot + /dos had the same size as swap. In this case, only / was a md device.

The problem still occured after a complete reinstall (including disk re-partitioning). After installing the system, even before updating it, I tried to back it up and it hung.


Hardware:
Motherboard ASUS A8V Deluxe (using the Promise controller in IDE operating mode)
RAM: 1 GB Corsair in Dual Channel (those beautiful ones with activity leds :) )
CPU: AMD Athlon64 3200+ Venice
HDD: 2 Seagate ST380817AS (80 GB, NCQ, SATA, 8 MB buffer)

I have an other HDD, it's a noisy Maxtor 120 GB, 8 MB buffer, IDE. It doesn't matter whether it's plugged or not: the problem persists.

Could it be a Linux software raid issue? Or a sata controller issue? HDD issue? Or is it me? :confused: 

If anyone has any idea or suggestion, please reply.

Edit: I booted the Ubuntu installed in the old Maxtor and tried:
e2fsck -c /dev/md0

As expected, everything locked up during the check. Can anyone help me?

---

### Post by tszanon on 2006-03-28
Hey people,

nevermind. Thanks to [this post]("http://ubuntuforums.org/showthread.php?t=52003&highlight=raid+sata+lockup"), now I know that my problem must be the Promise TX2Plus (Fake)RAID controller.

I'm gonna disable the Promise controller and use the VIA controller. If I'm lucky, everything is gonna be ok.

Cross your fingers!!! :D

Edit:
Oh yeah. I used "sudo e2fsck -c" on each ext3 MD, all at once. The system is still finishing the last (and biggest) MD (/home).

I guess everything is fine now. So, if you have this same problem, now you know that it probably is your "beautiful" Promise TX2Plus FakeRAID controller. And the answer for my question is "it's a controller issue".:mrgreen:

---

### Post by krakan on 2006-03-29
hey guys.. in case anyone happens to read this, I have two x SATA drives I'm planning to use RAID 1 on, I've read up on using MDADM to configure and initialise my array, and the disks are partitioned and ready to go - just where, for the screaming love of christ, is mkraid?

Anyone? At all? Please?

---

### Post by tszanon on 2006-03-29
According to everything I've read (and supposing I understood it all :) ), when using plain mdadm, the tools you will use to put the array online are not mkraid.

For that, you should use mdadm tools (mdadm, mdrun...). Unfortunately, I can't help you on that, because I created my arrays during system installation, so, the installer did the job for me, and I have no idea on how to use mdadm from command-line (well, at least not yet).

But I believe that's it: forget about mkraid and stick to mdadm, because that's what you're using to create your RAID arrays.

Good luck!

---

