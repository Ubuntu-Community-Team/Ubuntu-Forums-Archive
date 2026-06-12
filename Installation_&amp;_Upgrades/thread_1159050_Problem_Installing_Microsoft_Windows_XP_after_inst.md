---
title: "Problem Installing Microsoft Windows XP after installing Ubuntu 9.04"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by arnov007 on 2009-05-14
Dear Friends,

Right now I am using Ubuntu Linux 9.04, but I have mailny two problems.
1. Automatic Time Update which is not getting updated on next restart.

2. Installing Windows XP
When I put a bootable Windows XP CD it is showing me the following message:

[B]Windows XP Professional Setup

Setup did not find any hard disk drives installed.

Make sure any hard disk drives are powered on and properly connected to your computer and that any disk-related hardware configuration is correct. This may involve a manufacturer supplied diagnostic or setup program.

Setup cannot continue, to quit setup, Press F3[/B]

I tried installing after running a Primary Self Diagnostic test in the BIOS Menu but still it's showing the same error.

---

### Post by mdmarmer on 2009-05-14
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Mike

---

### Post by tacantara on 2009-05-14
When you install Ubuntu, it apparently does something to the hard disk drivers. Either that, or the unique file system "ext3/ext4) creates a conflict for XP, which utilizes the FAT32 & NTFS file systems. I can think of two options that will allow you to achieve the Ubuntu/XP machine that you're looking to set up:
 
1. Install VirtualBox (download it from the website - the version available in the Package Manager is the OSE version and is limited in available features). Once you have that installed, set up an XP virtual machine. I use this type of configuration to run XP, as a means to run the few programs that Wine doesn't run and there are no suitable open-source equivalents of).
 
2. Backup the essential files on your hard drive, then reformat it. Install XP, then install Ubuntu using the Wubi installer. Wubi allows you to set up a dual-boot system, thus no need for a virtual machine.
 
If anyone else has a solution that I've overlooked, please add you thoughts/ideas.

---

