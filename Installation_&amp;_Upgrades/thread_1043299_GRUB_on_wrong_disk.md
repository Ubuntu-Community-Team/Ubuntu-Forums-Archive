---
title: "GRUB on wrong disk"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by LtGordon on 2009-01-18
I have two internal hard disks, one for Windows and media storage, and one for various Linux/BSD distributions:

320GB PATA: (NTLDR - WinXP NTFS partition)
250GB SATA: (GRUB Multiboot - Linux/BSD)

This is a shared home workstation, so when I'm not on the computer I want to be able to leave the BIOS boot priority on the PATA-Windows disk so that it loads directly into Windows via NTLDR. But, when I switch boot priority to the SATA-Linux/BSD drive, I want to load GRUB off of that drive.

However, when I install Ubuntu it overwrites the MBR on the PATA-Windows disk, regardless of the current boot priority setting. Due to time constraints, I had to load the WinXP CD and replace the MBR with NTLDR.

In short: Ubuntu keeps writing the MBR to the wrong disk. How do I install GRUB on the SATA drive? Bonus: is it possible to make GRUB independent of any operating system, like on its own partition?

---

### Post by caljohnsmith on 2009-01-18
You can make a dedicated Grub partition so that Grub is independent of all your OSes, and the partition can be basically as small as you can make it, say ~5 MB. And about installing Grub to your Ubuntu SATA drive, just click the "advanced" button near the end of the Ubuntu installation process, and there you can specify to have Grub installed to /dev/sdb or whichever is the Ubuntu drive. If you want more specifics on how to make a dedicated Grub partition, how about first setting up a 5-10 MB ext3 partition, and post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

