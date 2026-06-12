---
title: "Installation on a newly replace hard drive..."
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by rosiny on 2009-10-08
Hey everyone,

I recently replaced my failing hard drive with a new Western Digital one, and decided to install ubuntu solely on this computer...

However, I attempt to install using 9.10 CD, and it doesn't seem to detect the Disk at all - i.e. I get to the partition menu, and it doesn't give me any choices for partitioning, just a blank screen. 

Any suggestions/help?

Thanks!

---

### Post by ajgreeny on 2009-10-08
With the live CD run ```
sudo fdisk -l
``` to see if the system sees it at all.

---

### Post by rosiny on 2009-10-08
It gives me the following output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table


Which I'm guessing means that it does detect my hard disk...

---

### Post by rosiny on 2009-10-09
Any ideas? =)

---

### Post by PrePenguin on 2009-10-09
> **rosiny said:**
> Any ideas? =)

Did the new Hard Drive come with a CD for set-up? You may need to check your bios settings also for new HD..

---

### Post by rosiny on 2009-10-09
The new hard drive did not come with a set-up disk or anything... How do I check my BIOS settings?

---

### Post by rosiny on 2009-10-11
Still haven't fixed the issue. Does anyone have any suggestions?

---

### Post by Bartender on 2009-10-12
Well, first thing I'd try is make a GParted LiveCD (link below sig) on your computer or someone else's.

Boot from the GPLCD.  GPLCD should see the WD HDD.  Format the entire drive.  At the very minimum create a primary ext3 partition.  Or set up a primary ext3 partition, then a big extended box, and create a partition inside the box as ext3, or whatever.

The point being, use a partitioning tool to create a file structure that the Ubuntu install CD "should" recognize.

---

### Post by mechro on 2009-10-12
Possibly an issue with Karmic...

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/449414](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/449414)

Try Jaunty.

---

### Post by rpete on 2010-10-06
Hi, I am having the same problem.  I took out my old hard drive and put in a new one, then ran the Ubuntu 8.04 DVD.  I was never instructed to partition the drive.  When I type sudo fdisk -l  or -lu in terminal the output clearly shows the new drive is recognized, listing its sectors etc but then states "dev/sda doesn't contain a valid partition table.  

What can I do? Do I need to download the application GParted?

---

### Post by vollmey on 2010-10-09
I am having the same problems with a drive that had 10.04 on it and now I am doing a fresh install to 10.10...  I can't get the installer to see the drive.

Any ideas?

---

