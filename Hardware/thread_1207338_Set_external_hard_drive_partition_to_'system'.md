---
title: "Set external hard drive partition to 'system'"
date: 2009-07-08
forum: Hardware
---

### Post by theayatollah on 2009-07-08
Hi everyone,
 
I'm wondering if I can do this: I have an external hard drive with a bunch of files on it that I need. I also need to install Windows 7 on a bunch of machines shortly. What I wanted to do is create a FAT32 partition and put the setup files for W7 on it, then boot from USB to install on the various machines.
 
I set up the two partitions on the external with gparted, then set partition with the W7 files to boot flag. I also had bootsect.exe recognize and set the particular drive with the W7 files.
 
When I boot, I get a black screen when it gets ported to the external. FYI other devices do work via USB, such as my Backtrack distro.
 
What I think is going on, is that the partition with W7 is not the "system" flag, although it is "boot".
 
You guys are smart, what do you think is the issue?

---

