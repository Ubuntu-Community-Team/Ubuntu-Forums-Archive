---
title: "Installing on an external Hard drive."
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by killpotts on 2009-03-08
Hey all, I am having troubles figuring out exactly how to install Ubuntu onto an external Hard drive. The internal Hard drive of this machine is pretty much dead. Ubuntu is capable of detecting it, but cannot mount it.

I have a 160 GB External, which is currently connected as "sdb1" and has one large partition on it.

The two partitions on the internal HD are listed as sda1, and sda2.

My problem happens on step 4 of Ubuntu 8.10 installation. It is only detecting the sda1 and sda2 to be partitioned ( which I know will not work, since that hard drive is busted. I have to wait until I get my new one in the mail, which I will likely just install windows XP on anyways. ) and does not detect the external drive as a possible selection ? Seems kind of odd since my external drive is the only one that I can mount and explore files on. 

My questions are these:

1. Do I need to do something with sdb1 with Gparted ? All of the data on this external is backed up on a different drive, so I do not mind if it gets deleted. The only option I get ( as in, not disabled ) for sdb1 is "create partition table". Do I need to do something here ?

and

2. I tried this before with a different problem, namely Grub error 21. What can I do to prevent Grub from trying to default install to the main ( internal ) HD and instead pointing to sdb1 ? I really don't want to go through fixing Grub errors again, and would like Grub to just point to the external right away. ( Btw, the name for this external HD is "OMEGA_ZEN" )

---

### Post by killpotts on 2009-03-09
Here is where I have gotten so far:

I found from elsewhere that I needed to change my external to the "ext3" type filesystem using Gparted. I did that.

It's detecting the external drive now at step 4, and I am able to click it. I can then get past step 5 ( putting my name in/password/ect ) but after that I run into a problem. One it starts installing it gets to a point at 5% for setting up partitions for the drive, but crashes. I now have a "crash report detected" "!" point at the top of my screen. I would post the crash report, but unfortunatly when I click on it it just goes away and does not show any report ( I have absolutely no idea where to find the report. take note that I am doing this from the live CD ). I tried again and it gave the same error - 5%, crash.

Specifically:
```


-Installing system-
"Partitions Formatting"

||||5%

creating ext3 file system for / in partition #1 of SCSI6 (0,0,0)

```
about 6 minutes later, it crashes. It seems to have done SOMETHING as when I open my external up in Gparted it now shows 2 additional partitions on the external drive: sdb2 ( extended ) and sdb5 ( linux swap )

This is what the new data from Gparted is in regards to my external HD:

the partitions on /dev/sdb are:

Partition:/dev/sdb1
Filesystem:ext3
Size: 143.26 GB
Used: 2.43 GB


Partition:/dev/sdb2
Filesystem:extended
Size: 5.78 GB



Partition:/dev/sdb5
Filesystem:linux-swap
Size: 5.78 GB


*I believe SCSI6 is what it calls my external HD


any ideas at all ?
???

---

