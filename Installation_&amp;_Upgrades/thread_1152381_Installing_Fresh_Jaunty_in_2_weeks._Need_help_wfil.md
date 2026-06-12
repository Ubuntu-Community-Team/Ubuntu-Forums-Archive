---
title: "Installing Fresh Jaunty in 2 weeks. Need help w/filesystems."
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by blackbird3216 on 2009-05-07
So, now the two weeks are up, and I have to do it tomorrow. The computer has a pre-existing vista installation which I will overwrite, and I am planning to use ext4 for everything except home. I tried booting up the computer w/ the Live Cd, and hitting the install icon. On the partition tab, I hit advanced, and then I see three things, each with the option to "format". What is this supposed to mean? Format to empty, or format to Ext4/etc. Also, On a 320gb hd, how do I make the separation between ext3 for home, and ext4 for everything else(except for swap, obviously). Thanks. :p

---

### Post by taurus on 2009-05-07
Haven't ran into any problem with ext4 so far so use ext3 if you wish.

---

### Post by blackbird3216 on 2009-05-08
Any other suggestions?

---

### Post by black_shadow on 2009-05-08
There are known issues with ext4 would stick with ext3

Mike

---

### Post by HyRax on 2009-05-08
> **blackbird3216 said:**
> Any other suggestions?

Ubuntu Jaunty 9.04 will default to Ext3 across the board during the install, but you can choose to have everything bar /home as Ext4. All you have to do is manually partition the drive during the installation process to separate elements of the filesystem out rather than go for "automatic" setup which generally rolls everything into one big partition.

In your case, create at least three partitions for Ubuntu, namely "/" (root filesystem), "swap" and "/home". Make the root filesystem Ext4, swap is swap, and make /home Ext3.

The issues with Ext4 centre around data not being yet written to the drive in the event of a power loss. The easy fix for this is simply to get a UPS for your PC - they're cheap and guarantees your PC won't suffer a power loss in the event of dirty power or a blackout. This is what I use. After that, your only risk would be if the PC crashes in some horrendous way that you had to hit the reset button and data had not yet been written to the drive, which for Linux is a rarity.

As for Compiz, it's dependent on whether or not you have an OpenGL-supported gfx card on-board, ie: if it's ATi or NVidia, you should be fine. If it's Intel, Compiz may work but Jaunty's Intel gfx implementation is a little slow at the moment.

---

### Post by blackbird3216 on 2009-05-22
Going to do it tommorow. Need help.

---

### Post by HyRax on 2009-05-23
> **blackbird3216 said:**
> Going to do it tommorow. Need help.

With what?

---

### Post by blackbird3216 on 2009-05-23
> **HyRax said:**
> With what?
well, I don't know how to format the HD(which already has Vista), completely removing the Vista partition, having a home partition as ext3, and root as ext4, while splitting the 320gb HD proportionally. How big should the swap be?

The biggest problem I am having is I don't know how to do the aforementioned.

---

### Post by HyRax on 2009-05-23
> **blackbird3216 said:**
> well, I don't know how to format the HD(which already has Vista), completely removing the Vista partition, having a home partition as ext3, and root as ext4, while splitting the 320gb HD proportionally. How big should the swap be?

The biggest problem I am having is I don't know how to do the aforementioned.

Well, are you wanting to keep Vista or dedicate the entire drive to Ubuntu?

Swap size depends on how much memory you have. If you have 1GB or more, then 512MB is more than sufficient for swap because your system will hardly ever touch it. If you have less than 1GB RAM, then I'd recommend 1GB for swap.

---

### Post by blackbird3216 on 2009-05-23
> **HyRax said:**
> Well, are you wanting to keep Vista or dedicate the entire drive to Ubuntu?

Swap size depends on how much memory you have. If you have 1GB or more, then 512MB is more than sufficient for swap because your system will hardly ever touch it. If you have less than 1GB RAM, then I'd recommend 1GB for swap.
Ok, so since the computer has 2gb of memory, then I will only use a 512mb swap. How big should / or Home be? I would really appreciate if you could guide me through the process, everything after the keyboard selection. Thanks.

---

### Post by HyRax on 2009-05-24
> **blackbird3216 said:**
> Ok, so since the computer has 2gb of memory, then I will only use a 512mb swap. How big should / or Home be? I would really appreciate if you could guide me through the process, everything after the keyboard selection. Thanks.

What you allocate really depends on your own needs - one glove does not necessarily fit everyone.

For a typical desktop that is going to see general day to day use (ie: you're not a programmer, kernel hacker, file hoarder, etc), I would suggest the following. I'll assuming you're installing Ubuntu Jaunty 9.04:

```

Mountpoint   Size                Format as
-----------------------------------------------
Swapspace   512MB                Swap
/boot       100MB                EXT2
/             8GB                EXT4
/home       Remainder of drive   EXT3 or EXT4
-----------------------------------------------

```

Choosing EXT3 or EXT4 for /home is purely up to you. If you can ensure that you're not going to get some random blackout before you safely shut off your PC (ie: you have a UPS or something connected to your PC), then go for EXT4, otherwise stick with EXT3.

Ubuntu's base OS and associated desktop software (in "/" aka "root")installs in 2GB worth of disk space. You need at least another 2GB to allow for things like future system updates, so making the root filesystem 8GB should be more than enough to allow for updates and any additional programs you want to install such as games etc.

/boot only needs 100MB to store the kernel files and that's it. The reason you would choose to keep this separate is that should the rest of the drive suffer a corruption, you could at the very least boot up your system to a root prompt with a separate /boot partition. /boot is generally formatted as EXT2 because it will be rare that anything new gets written to /boot thus you don't need the journaling capabilities of EXT3 or EXT4, but there's no harm in using either of those filesystems either. Up to you.

---

