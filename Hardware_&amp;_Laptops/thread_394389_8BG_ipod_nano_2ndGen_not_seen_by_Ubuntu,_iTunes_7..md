---
title: "8BG ipod nano 2ndGen not seen by Ubuntu, iTunes 7.1.1 messing things up?"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by alberto.m.vasquez on 2007-03-26
Hi,

I have Ubuntu 6.1 running. I just got a brand new 8GB ipod nano 2ndGen.
I initialized it under Windows XP using the latest iTunes version available
(7.1.1). The nano works perfect under XP.

Problem is that when I plug the ipod to the USB port, Ubuntu does
not see it. So I tried to mount it by hand (see lines below) and it looks like
the new iTunes formats the nano in a way that is not yet recognized by
Ubuntu. Can someone help? Thanks anyway! Here's my try to mount it:

------------------------------------------------------------------------------------------------------------
su: mount -t vfat /dev/sda /media/ipod 
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
------------------------------------------------------------------------------------------------------------
su: dmesg | tail 
[17249435.492000] sda: Write Protect is off
[17249435.492000] sda: Mode Sense: 68 00 00 08
[17249435.492000] sda: assuming drive cache: write through
[17249435.492000]  sda: sda1 sda2
[17249435.500000] sd 2:0:0:0: Attached scsi removable disk sda
[17249435.500000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17249436.676000] FAT: count of clusters too big (493934)
[17249436.676000] VFS: Can't find a valid FAT filesystem on dev sda.
[17249442.444000] FAT: count of clusters too big (493934)
[17249442.444000] VFS: Can't find a valid FAT filesystem on dev sda.
------------------------------------------------------------------------------------------------------------

---

### Post by will_in_wi on 2007-03-26
Try mounting /dev/sda1 or /dev/sda2.

---

### Post by alberto.m.vasquez on 2007-03-27
I just did it and it worked with sda2! TNX A LOT!
So I added this line to /etc/fstab:

/dev/sda2       /media/ipod     vfat    rw,user,noauto  0       0

so any user can "mount /media/ipod" or "eject /media/ipod"
Why is that it can't get automounted whenever I plug it?
Also, when I mount it by hand no ipod icon shows up
in my desktop.

In any case, now gtkpod sees the ipod and i successfully transferred
music to it!!! 

Thanks SO MUCH!

A.

p.s oh, also AmaroK or Banshee can't see the device.

---

### Post by surfbywire on 2007-04-13
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/hal/+bug/66068](https://launchpad.net/ubuntu/+source/hal/+bug/66068) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **alberto.m.vasquez said:**
> I just did it and it worked with sda2! TNX A LOT!
So I added this line to /etc/fstab:

/dev/sda2       /media/ipod     vfat    rw,user,noauto  0       0

so any user can "mount /media/ipod" or "eject /media/ipod"
Why is that it can't get automounted whenever I plug it?
Also, when I mount it by hand no ipod icon shows up
in my desktop.

In any case, now gtkpod sees the ipod and i successfully transferred
music to it!!! 

Thanks SO MUCH!

A.

p.s oh, also AmaroK or Banshee can't see the device.


I bought an 8GB 2nd generation iPod last weekend. In the beginning I couldn't get things to work with Edgy and I was seeing what you were seeing.... After poking around on the net, I found that there is an issue with the hal module in Edgy. It was seeing the ipod as a raid device. See the bug url.

After I installed the fix everything worked perfectly. Everytime I connect the pod, it auto mounts the ipod and it shows up on my desktop. Plus banshee even recognizes it.

Here's the fix:
[http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/](http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/)

---

### Post by alberto.m.vasquez on 2007-04-20
hey, thanks a lot!

I just came out with another solution, I upgraded to ubuntu 7.04, 
and everything works just perfect now.

not only my ipod is automatically recognized
and mounted, but also the latest versions
of rythmbox, and gtkpod, gpixpod, work much better

cheers!

---

