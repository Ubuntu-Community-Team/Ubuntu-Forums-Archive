---
title: "Partition Question"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by johns996 on 2006-08-23
My job just issued me a laptop and, having little work-related use for it, I decided to make it a quintet-booting monster.  In theory I thought this would be a breeze with the friendliness of modern distros, but i've run into some problems.  Here's the breakdown.

I wanted to install WinXP (for the occasional work-related task), Ubuntu, Fedora Core 5, SUSE, and FreeBSD.  After my first round of installs (Ubuntu and Win), I realized that I can only have four primary partitions.  So I deleted my three ubuntu parts and created one big extended partition leaving the windows one alone.  I installed Ubuntu to the extended and it seemed to work ok.  

My questions are, can I share the swap partition between distros?  Will I have a problem running Ubuntu in an extended partition?  Has anyone else tried to install this many distros on one drive?  Is it even possible?

---

### Post by mlind on 2006-08-24
Yes, you can safely share a swap partition between (all ?) distros. I share swap and /home and /boot with 2 Ubuntu distros and with one Debian.

I've setup LVM and only /boot is outside of it.

You shouldn't have any problems running Ubuntu on extended partition as far as I'm aware of. I have 3 different distributions on one drive, all using a shared swap, /boot, /home and GRUB (on MBR), so I don't see it wouldn't work for you as well.

---

### Post by johns996 on 2006-08-24
Thanks for the reply.  So far I've gotten Win, Ubuntu, SUSE, and Fedora Core installed without any problems.  It is kind of annoying that all of the other installers don't allow their OS to be installed into an extended partition, with the exception of Ubuntu.  I'm hoping FreeBSD will allow this because I'm out of primary partitions.

I haven't encountered any problems sharing a swap between the partitions yet.  I haven't set up a /boot or /home partition for any distro.  I'm just letting each write everything to their root.

---

### Post by mlind on 2006-08-24
> **johns996 said:**
> 
I haven't encountered any problems sharing a swap between the partitions yet.  I haven't set up a /boot or /home partition for any distro.  I'm just letting each write everything to their root.

How are handling the GRUB issues when every distro has it's own /boot and can't see other distos kernel images, because those are on separate /boot (partition) ? Or do you manage your GRUB menu manually somehow?

---

