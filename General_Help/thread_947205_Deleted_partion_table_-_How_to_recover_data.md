---
title: "Deleted partion table - How to recover data?"
date: 2008-10-14
forum: General Help
---

### Post by sundar22in on 2008-10-14
Hi,

I was using Smart Boot Manager (SBM) ([http://btmgr.sourceforge.net/download.html](http://btmgr.sourceforge.net/download.html)) in USB stick and it screwed my machine. I had windows XP, now after using SBM i am getting an error message "Error loading the operating system".

I want to recover some files which are available in the hard disk. I used ubuntu/knoppix and it shows the hard disk, but I could not mount any partitions. fdisk -l command does not list anything related to the partitions. Is there any tools for recovering some files from hard disk. I want to copy few files and I can reinstall ubuntu after that. Any help on recovering the files is highly appreciated.

Will GParted be useful, or systemrescueCD?? I have no clue. Please help.

Thanks in advance.
Sundar:confused:

---

### Post by hyper_ch on 2008-10-14
try *gpart*

---

### Post by Sef on 2008-10-14
> Will GParted be useful, or systemrescueCD?? 

Best would be [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  

From its Wiki:

> **TestDisk** is a *powerful* free data recovery software! It was primarily designed to help **recover lost partitions** and/or **make non-booting disks bootable again** *when* these symptoms are caused by *faulty software*, certain types of *viruses* or *human error* (such as *accidentally* deleting a Partition Table). Partition table recovery using TestDisk is really easy.

---

### Post by hyper_ch on 2008-10-14
*gpart* can restore partition tables. I used it a week ago :) and it's not to be confused with *gpart**ed***

---

### Post by sundar22in on 2008-10-14
Thanks for your pointers.

Currently I do not have a host OS, also I cannot move my hard disk available in my laptop to other machine. I have a USB pendrive and Can I boot TestDisk or other tools from Pendrive for recovery?

Thanks again.

---

### Post by hyper_ch on 2008-10-14
well, I mean with "partition tables" the ones indication primary partitions, extended partitions, logical partitions... just to be clear :)

---

### Post by sundar22in on 2008-10-14
Can i use qpart without having any host os from USB stick?

---

### Post by hyper_ch on 2008-10-14
I was talking about **g**part, not **q**part - just to make sure. You can run it from a live cd... boot the live cd, install gpart with synaptic or *sudo apt-get install gpart* and run it in a terminal.

I used it a week ago when I deleted the master boot record of one of my harddisk and forgetting that it also deletes the partition tables/definition or rahter makes them unusable. The individual partitions, however, were not touched! They were ok... just the system didn't know anymore where each partition was. So gpart can help you make the system aware again that you have primary and extended and logical partitions on there. It will NOT restore data within partitions.

---

