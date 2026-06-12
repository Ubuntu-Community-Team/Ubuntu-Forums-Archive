---
title: "boot partitions"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2009-01-15
Hi all,

I have recently read that

 Linux /boot partition should be 16-32 MB, and it must be within the
first 1023 cylinders or 8 GBytes of your hard drive. It does not
matter whether /boot is a primary or logical partition.

 can any one explain to me why this so ?

 what is the standard size for boot partition ?

---

### Post by Partyboi2 on 2009-01-16
If Ubuntu is going to be your only os or if you plan to dual boot you don't really need a separate /boot partition. But if you are going to create one 50mb should be suffiecent.

---

### Post by Herman on 2009-01-16
:confused: I'm confused about whether you mean a 'separate /boot' or a 'Dedicated GRUB' partition.

If you're talking about a 'Dedicated GRUB Partition', I agree with Partyboi2.
GRUB by itself is very small and in that case, 50 mb would be fine. Even 16-32 mb would probably do. I usually make mine 100 mb or so, just to be sure, in case I want to add some splashimages and other stuff.
A 'Dedicated GRUB Partition' is easy to set up, it can be made anytime, and contains only GRUB files and so it is smaller than a 'Separate /boot (and a lot more useful if you want to multi boot).
GRUB in it's own partition will be 'operating system independant'. It's really a small operating system itself.  From there you can chainload any hard disk or partition boot sector in the whole computer, and add or remove disks and operating systems as you please. A 'Dedicated GRUB Partition' can be located anywhere on a hard disk, and even sometimes on a non-first hard disk. Normally the stage1 for it is installed to MBR in the first hard disk. 

On the other hand, if you're talking about a 'Separate /boot Partition', that's an entirely different kettle of fish.  I'd make mine around 1/4 GB at least, or 1/2 GB maybe, so you'll have room for a few kernels and initrd.img files. Normally, you create a 'Separate /boot Parition' when you are installing the operating system, and it will be registered in /etc/fstab as the /boot partition (belonging to that particular operating system). It's not normal for modern computers these days to need a separate /boot. The main purpose of making a separate /boot partition was to fence in the Linux kernel close to the start of the hard disk in old computers with BIOS hard drive size limits. (Some old BIOSs could only map the first 8.5 GB of a hard disk). The separate /boot partition was a cure for GRUB Error 18. 
A disadvantage of the separate /boot partition is that it's hard to share between two or more Linux distros if you decide to dual boot or multi boot. Only one distro can own the menu.lst file, so you need to configure the other OS with a modified update-grub script and rename one of the menu.lst files to some other name.
Are you installing in a computer that's more than around 10 years old?

---

