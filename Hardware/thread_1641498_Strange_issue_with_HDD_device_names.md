---
title: "Strange issue with HDD device names"
date: 2010-12-09
forum: Hardware
---

### Post by xgrnsxs on 2010-12-09
Hi all

I recently installed my first version of Kubuntu 10.10 a few weeks ago to give another linux dist a try. I was using SuSE Linux a long time and was curious about some other Distros.

I`m a long term Linux user and so far not a noob but haven`t been able to figure out a solution to a very special problem to which I didn`t find much on the internet so far.

At first, here comes the hardware listing:
I'm using a PC with an Intel Core2 Quad and Kubuntu 10.10 64bit.
6GB RAM
3 Harddisks physically connected to Sata1 to Sata3
each one with several Partitions

When i installed Kubuntu 10.10, i missed to configure the mountpoint of 3 NTFS Partitions of my Win installation. So i manually added them to fstab.
Right then i already wondered why HDD and partition Device nodes began with sdf to sdh instead of sda to sdc.

I entered a mountpoint to /dev/sdf3 (My Windows System Drive)

a mountpoint to /dev/sdg2 (My Windows Data drive where my Documents and tools reside) 

and a mountpoint to sdh1 where Musik etc resides.

Everything went fine until a few days later. Suddenly I got a message that said: could not mount /dev/sdg2 because the Drive did not seem to be there anymore.
The linux partitions (reiserfs) are mounted by device-ID so changing of their device nodes etc does not affect mounting. So the System can boot up cleanly except the NTFS partitions.

I investigated and found out, that, without changing anything related to hardware or in the Bios, the Device mapping had changed.  Now the HDD physically connected to SATA1 is represented by /dev/sda and Sata2 is represented by /dev/sdb and so on.
So i changed fstab but after a reboot everything changed again and HDDs again started with /dev/sdf.
All this happend without changing hardware. Since then it may take just a reboot to change the mapping. It changes spontaneously and does not always happen. Sometimes it changes, then a few days the configuration is stable und suddenly it changes again and may stay a few days or not...

I tried to mount the partitions by device-ID to get rid of the /dev/sd* stuff but this doesn`t seem to work because of restrictions in the NTFS-FS-Driver.

I never had such problems with different Distros of Linux and i wonder how this can be. I always thought, that the physical Port of SATA1 would be constantly represented be /dev/sda since it is a matter of addressing. Is it possible that addressing of SATA-ports may change from reboot to reboot?

Does anyone have an idea how to fix this?
(I am not going to get rid of Windows since I use it for gaming and need these Partitions in Windows too! *gg* ;))
I would really appreciate your help since this problem is very annoying

With kind regards
xgrnsxs

---

### Post by xgrnsxs on 2010-12-13
No one out there with the same Problem?

This behaviour doesn`t occur on other Distros and i do not have any  more ideas how to track this down.

If you need any further information, please let me know...

It would be very nice if someone has an idea how to solve it. I would like to keep Kubuntu. It`s a very annoying Problem and without a solution to this, i think i will dismiss Kubuntu, even though i felt quite comfortable with it when it comes to any other aspects of usability.

So far, i hope this will not lead to nowhere...

---

