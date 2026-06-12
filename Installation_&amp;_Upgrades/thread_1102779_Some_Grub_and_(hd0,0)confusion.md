---
title: "Some Grub and (hd0,0)??confusion"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by neilevan814 on 2009-03-22
Okay, just started thinking about installing a second linux distro on my Hardy disk. 

A little background:  *First I installed 1 250Gb disk on this system and installed Hardy 8.04 onto it*
                      *Then, I a couple weeks later installed a 200Gb disk which I set up purely as a backup drive*.

Okay, Gparted recognizes my Hardy disk as /dev/sdb and my backup as /dev/sda

My menu.lst is set for (hd0,4) 
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=cbbc23cf-3928-41de-ab45-1603c26867ca ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

It is my understanding that (hd0,x) corresponds to /dev/sda and (hd1,x) would refer to /dev/sdb.  This is not true in my case, so when I install the next distro and it searches for the MBR in the first disk will it know that /dev/sda is just a media disk and that in fact /dev/sdb is the disk to search out grub from?  

What do you think????

neil@neil-htpc:~$ sudo /sbin/fdisk -l
[sudo] password for neil: 

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabb01645

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24792   199141708+   5  Extended
/dev/sda5               1       24792   199141677   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ccc4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15935   127997856    5  Extended
/dev/sdb5               1        2550    20482812   83  Linux
/dev/sdb6            2551        5100    20482843+  83  Linux
/dev/sdb7            5101        5482     3068383+  82  Linux swap / Solaris
/dev/sdb8            5483       15935    83963691   83  Linux

---

### Post by meierfra. on 2009-03-22
> It is my understanding that (hd0,x) corresponds to /dev/sda and (hd1,x) would refer to /dev/sdb.

No, (hd0) is the drive you are  booting from, (hd1) is the second drive in the boot order in the bios, and so on.


> will it know that /dev/sda is just a media disk and that in fact /dev/sdb is the disk to search out grub from? 

No.  The installer has no knowledge of the boot order in the bios.  So it probably will assume that /dev/sda is the boot drive. But any distro, I have ever tried, lets  you specify  where to install grub. But still, in complicated  situations,  menu.lst might be wrong and/or  grub might get installed wrongly.

Starting with 8.10 Ubuntu uses "uuid  xyz..." instead of "root (hdx,y), which has eliminate most grub  errors made by the installer.

I recommend to  install grub to the boot sector of partition containing your new  Distro. Then you can just chainload  the new Distro from your existing Grub menu and even if the installer of the new Distro messes up,  you still will be able to boot into you old system.
And as long as you can boot your old system, it should be fairly easy to fix any  problems caused by the installer.

---

### Post by dandnsmith on 2009-03-22
There are some interesting little files associated with the GRUB installation, which get set up as it installs.
A probe is performed, and the results get recorded (I think devices is one of the files, in the grub directory). These results are then used when GRUB is used to boot, and can have interesting results when the disk fs get re-ordered.
I seem to recall that, in the absence of the files, GRUB will perform a probe of the BIOS in order to get things done.

---

### Post by meierfra. on 2009-03-22
> GRUB will perform a probe of the BIOS 
Grub  describes this process as  "Probing devices to guess Bios drives"

So Grub probes the devices create by the kernel.  It does not  probe the bios. The kernel does not have any information about  boot order in the bios. So  Grub does not any have  way to determine the actual  boot order in the bios.  
As a result, Grub's guess is often wrong.

> A probe is performed, and the results get recorded (I think devices is one of the files, in the grub directory). These results are then used when GRUB is used to boot,

The results of the probe  are used to determine the position  of the  drive containing the stage 2 file.  This position is then recorded in the first few sectors of the hard drive (the partition number is also recorded here).

The exact result of the probe are recorded in  device.map.
The device.map has two  main  purposes:

1) inform the user of the results of the probe.

2) the user can edit   device.map and use it as  an optional argument to "grub" and "grub-install" to correct the mistakes by the probe.

But device.map is not  being  used during boot up.

> can have interesting results when the disk fs get re-ordered.

Absolutely true.

---

### Post by dandnsmith on 2009-03-22
I'm glad to see you say that about recording the position and partition number in the stuff written to the boot sector - I've known for a while that it had to be there, but have never found a good description to tell me where (and I'm not about to acquire and examine source code to find out).

I'm a little puzzled about what you say about GRUB and probing - when using GRUB it cannot use any kernel info, as the kernel is not yet loaded (that being part of GRUB's work), which leaves it only 2 possibilities: the BIOS records, and stuff written when the GRUB loader was installed.

---

### Post by meierfra. on 2009-03-22
> I'm a little puzzled about what you say about GRUB and probing - when using GRUB it cannot use any kernel info, as the kernel is not yet loaded (that being part of GRUB's work),

You have to look at it this way:  There are two grubs:

Grub I:  The grub which is doing the actual booting

Grub II:  The grub shell invoked via "sudo grub" or "sudo  grub-install" 

Grub I gets its information from the bios. So Grub I  orders the drives in the same way as the bios.

Grub II gets its information from the kernel. So Grub II orders the drives in the same way as Ubuntu.
Grub II  is in charge of  writing the hard drive and partition information into the first few sectors of the boot drive.

Now suppose you have two hard drives, HD1 and HD2. Say HD1  is the first in the boot order in the bios  and HD2  second.
So  Grub I  thinks

HD1=(hd0)
HD2=(hd1)

Now suppose the kernel  sees HD1 as /dev/sdb   and HD2 as /dev/sda. So "Grub II" will see HD1 as  the second  hard drive and HD2 as the first
Thus "Grub II" thinks:

HD1=/dev/sdb=(hd1)
HD2=/dev/sda=(hd0)

Suppose further that Ubuntu  is on /dev/sda5. Then "GRUB II" sees the Ubuntu partition as (hd0,4).  So "Grub II" will write the numbers "0" and "4" into the first few sector of the boot drive HD1=/dev/sdb

During booting, "Grub I" will read the numbers 0 and 4 and so will look for Ubuntu on the fifth partition of (hd0). But "Grub  I" thinks (hd0) is HD1, that is /dev/sdb. So Grub I looks for Ubuntu on  /dev/sdb5 and booting fails.


I hope this makes some sense and is not too confusing.

---

### Post by neilevan814 on 2009-03-22
Hmmmmm...well, that is all a lot to take in.  I will digest it a bit and probably experience will end up being my best teacher.  If I have a problem.  I will again ask for for help.  Thanks all for your input and knowledge.

---

### Post by meierfra. on 2009-03-22
> Hmmmmm...well, that is all a lot to take in

Here is the short answer. Don't worry about it.  Probably you won't run into  any problems, and even if you do, it can be  easily fixed after you installed the new Distro.

---

### Post by dandnsmith on 2009-03-23
meierfra -
thanks for taking the time and trouble to give that explanation.

---

