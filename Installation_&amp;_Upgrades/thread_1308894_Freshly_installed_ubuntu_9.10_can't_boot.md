---
title: "Freshly installed ubuntu 9.10 can't boot"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Maxei on 2009-11-01
Hi, I downloaded the ubuntu 9.10 final and made a CD. During the installation, all the partitions of the previous Ubuntu 9.04 were formatted to Ext4 using the ubuntu installer, as usual, and everything went smooth until the time to boot for the First time.

At boot, I read the message:

"GRUB Loading stage 1.5."
"GRUB loading, please wait..."

So I waited, and waited for about 5-10 minutes. Nothing.

It seems that the GRUB program is not loading after all? 

Can you help please?

---

### Post by Maxei on 2009-11-01
Maybe I have messed up the master boot record (MBR) sector? I have set one partition  /boot and when asked where to put the boot loader I chose this partition. Any ideas?

---

### Post by Lucky. on 2009-11-01
I don't want to get dogged for pumping this over and over in each thread, but it might help...

[Karmic Boot Issue + SATA](http://www.ericforyan.com/index.php?node=21)

> ...Koala detected the fake-RAID even though my BIOS wasn't set to use it.  I know more than a few PCs with SATA drives that are set to IDE mode rather than RAID mode...especially computers with single drives only.  Fake-RAIDs are becoming more and more commonplace since SATA became popular.  If you have boot issues with Karmic, take a look at your BIOS and see if you can't configure your SATA devices differently.

---

### Post by Maxei on 2009-11-01
I found the mistake I did. During install and after disk formatting, I chose to install the boot loader in the "/boot" partition. This of course did not override the previous GRUB version installed in the master boot record (MBR) of the hard disk, so that GRUB could not find the previous old kernels.

So I did a new install and this time allowed to install boot leader into the default device (hd0). That did the trick.

So, may I ask if the "/boot" partition is now obsolete in Ubuntu? If not, what is it for?

These kind of details are easy to forget .

---

