---
title: "corrupted hard drive"
date: 2019-09-07
forum: Hardware
---

### Post by debroos on 2019-09-07
Cutting a long story short, is there any way I can format the hard drive on an eeepc from a USB flash drive, on which Ubuntu, Lubuntu and GParted are now unable to find any partitions following the installation and removal of the Cloudready chrome OS? Thanks for reading

---

### Post by Dennis N on 2019-09-07
Start by trying to make a new partition table using gparted working from live Ubuntu media. Then you can create new partition(s). Finally, formatting these for your intended use.

---

### Post by Autodave on 2019-09-07
I don't know exactly what model you have, but I used to have one that would not boot from a USB stick.  However, it would boot and install Xubuntu from an external DVD.  Was kinda weird, but it did work.

---

### Post by TheFu on 2019-09-07
I had an Asus Eee (Atom N270 CPU). It worked like any other laptop, just a little slower and with a 600p screen.
It booted from USB fine, so I could run a lite XUbuntu desktop and do any maintenance or emergency fixes needed.  I might have run Lubuntu then, I don't remember.

CloudReady is ChromiumOS and has 11 partitions on a GPT formatted drive, normally.  If you don't see those partitions from a USB-boot "live" Ubuntu, I'd guess there is a hardware issue.  That could be a loose connection or a dead SSD.

---

### Post by debroos on 2019-09-07
Many thanks to you all - It's now a work in progress (I hope).  Ubuntu booted up from CD after around an hour, with 82 errors scrolling up the screen at the outset. Gparted found 27 partitions, all of which it's finally deleted, apart from an unallocated partition of 149 Gb. Each deletion was preceded by three "lib parted bug found - I/O error during read on /dev/sda" messages, ending with a "Backup GPT table is corrupt, but primary appears OK so that will be used." I hit ignore for all the I/O error messages and OK for the last ones which I hope is the ideal response.  I'm fairly clueless with Linux, but optimism favours - now all the partitions are deleted - a crack at creating partitions for Ubuntu. It's been an interesting four hours watching the process :D

---

### Post by TheFu on 2019-09-07
Check the system logs for the errors. 
Look up each to see what it is.  Disk/storage errors should never be ignored.
[LIST]
[*]bad cable
[*]bad controller
[*]failing disk
[/LIST]

It needs to be fixed regardless of what is causing the problem.

---

### Post by Skaperen on 2019-09-07
i would "zero zap" the first few megabytes of the target hard drive, if not the whole thing (depending on how much of a hurry i was in) before repartitioning.  i like to keep it simple but still have /home kept separate, so i make / on p1, swap on p2, and /home on p4, using MBR if i can.  i used to do more complicated stuff with one time as many as 36 partitions with Slackware, OpenBSD, FreeBSD, and LFS on there.  then i realized that shutting down just to work on something else slowed me down way too much.  so i went with VMs.  and that was way back in time.

---

### Post by Dennis N on 2019-09-07
> Gparted found 27 partitions, all of which it's finally deleted

If you create a new partition table first thing, any partition structure on the disk will be lost. This may take 5 seconds or less. So you don't really need to delete them and the entire disk will show as unallocated. You can then go ahead and create new partitions.

---

### Post by debroos on 2019-09-09
Thanks again for all advice.  Stressing at the outset that my competence  with linux is very limited, I suspect the errors on the drive were the  result of the Cloudready OS. I have installed Ubuntu and Lubuntu on the  same machine several times over the years, all of which would work for a  while then go haywire for one reason or another - "..attempt to write  outside hd0" being fairly common, which was the last message received  around three weeks ago, following two days of working from a new  installation of Ubuntu 14.05.  It was this failure that prompted the  trial run of Cloud Ready OS. The scrolling error messages on the startup  screen have only happened since then. I have tried a fresh install of  Ubuntu 14.05, which looked promising, but it hung and ceased activity at  the Grub installation. I pulled the plug after three hours.  I've just - almost -created a partition with Gparted, but it has been unable to complete the process with the message "error fsyncing/closing /dev/sda1: input/output error".  Repeated 'ignore' button produces "input/output error during read on dev/sda."  Would it be possible to 'simply' wipe the disc with a mother of all formats from a flash drive?  I have no OS or material that needs to be saved.  Thanks again for your support

---

### Post by slickymaster on 2019-09-09
Thread moved to **Hardware** for a better fit

---

### Post by TheFu on 2019-09-09
Dude, re-read post #6.  You have a hardware issue that won't get better until you fix it. 

Also, ubuntu 14.04 is EOL and has been a few years. 18.04, probably the Lubuntu version, is what you should start with today - AFTER - fixing the hardware issue.

---

