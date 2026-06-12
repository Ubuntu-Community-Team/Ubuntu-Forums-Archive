---
title: "Software RAID5 and moving machine"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by sdennie on 2008-02-06
I've recently moved and couldn't bring my machine along but was able to take my 4x500G disks with me.  They are partitioned for software RAID5 that I setup using the Ubuntu 6.06 alternate installer.  Now I've got a machine that's running Ubuntu 7.10 on 2 disks (RAID0) on the onboard SATA controller and I'd like to buy a 4xSATA PCI-Express controller and hookup the 4x500G disks.  So, my questions are as follows:

1) Does the order in which I hook the disks up to the controller matter?  I numbered the disks when I took them out of the old machine so, I at least know the general order in which they used to be hooked up.  Does it matter?

2) It's been a few months but, I believe I setup the disks with independent /boot partitions, RAID1 root partitions and RAID5 for the rest.  Will I be able to simply mount one of the RAID1 root partitions from my current setup, copy the config files for the RAID setup (probably edit them to point at the right places) and be on my way?

I've got about a terabyte of data on the disks so I'm hesitant to just pop them in and see what happens.  Any advice you can give for transporting a software RAID5 setup that used to be self booting from other partitions on the disks to another machine would be really useful.

---

