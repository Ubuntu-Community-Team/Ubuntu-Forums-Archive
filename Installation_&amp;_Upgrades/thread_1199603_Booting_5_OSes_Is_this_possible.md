---
title: "Booting 5 OSes? Is this possible?"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by hyperyoda on 2009-06-29
I wish to setup on the same hard disk (500GB):

Ubuntu 9.04 (64 bit)
Debian 5.01 (64 bit)
MS Windows Vista Home Premium (64 bit)
MS Windows 98 (32 bit)
MS Windows XP (32 bit)

I want to allocate 50GB for each.

1) Is this possible?
2) How do I setup grub (or lilo) to do this?
3) What order do I install each?
4) How should I handle setting up the partitions?
5) Any special tips?

Zach

---

### Post by kristian on 2009-06-29
1) Yes.

2) Just as usual, for your gnu/linux systems you specify which root partition to use with either root (hd?,?) or uuid ?... and also you supply root=/dev/???? to the kernels. For the windows installations you use something called chainloading. I don't have any working configuration on me right now but it's nothing unusual so you should be able to find it in the manual.

3) I think you should consentrate on getting the Windows installations working first (you need to get the windows boot manager to work for all 3 systems).

4) You need to have the windows partitions as at the first three partitions. And then put the gnu/linux related stuff in the extended partition table.

---

### Post by /////// on 2009-06-29
Yes this is possible. You should install the operatin systems in this order: Win 98, Win XP, Win Vista, Debian, Ubuntu (first to last)

You may have to edit your bootloader configuration file afterwards if some operating systems don't work.

---

### Post by paul_be on 2009-06-29
good luck let us know how it goes:)

---

### Post by WRDN on 2009-06-29
You can do this. Windows must be installed on a disk with the msdos disk label, which allows for a maximum of 4 primary partitions. Windows must be installed on a primary partition, so I would recommend the following installation order: Windows 98, Windows XP, Windows Vista, Debian, and finally, Ubuntu.
Debian and Ubuntu must be installed within an extended partition (create 2+ logical partitions within the extended partition).

---

