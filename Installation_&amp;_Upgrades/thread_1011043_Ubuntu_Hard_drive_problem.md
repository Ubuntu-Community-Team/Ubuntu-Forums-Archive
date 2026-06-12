---
title: "Ubuntu Hard drive problem"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by mclane20032001 on 2008-12-14
I am pretty new to Ubuntu.

Just got a new 1TB hard drive to upgrade my system. I first took out the old drive to just start with a fresh install of ubuntu on the new drive. I boot from the CD and get to the part where you partition the drive and nothing shows up. Just the partitioning tool and nothing in the window.

I boot from a windows xp disk and the hard drive shows up and I am able to partition. I dont install windows.

I put the old drive in as the master. I boot from the old hard drive with ubuntu on it. Go to Gparted to see if I can partition the new drive there but it does not show up.

I run sudo fdisk -l and it only shows the old hard drive.

I have no idea why ubuntu can't see the drive since it shows up in my BIOS and the Windows installer can see it.

---

### Post by logos34 on 2008-12-14
experiment with different disk detect settings in the Bios--i.e. ahci vs. ide legacy mode, lba, auto, etc.

---

### Post by Mark Phelps on 2008-12-15
OK, the drive "shows up" in the BIOS, but how big does it say it is?  Some older BIOS's will "see" the drive but will not recognize the full capacity.

---

### Post by joff13 on 2008-12-15
> **mclane20032001 said:**
> I am pretty new to Ubuntu.

Just got a new 1TB hard drive to upgrade my system. I first took out the old drive to just start with a fresh install of ubuntu on the new drive. I boot from the CD and get to the part where you partition the drive and nothing shows up. Just the partitioning tool and nothing in the window.

I boot from a windows xp disk and the hard drive shows up and I am able to partition. I dont install windows.

I put the old drive in as the master. I boot from the old hard drive with ubuntu on it. Go to Gparted to see if I can partition the new drive there but it does not show up.

I run sudo fdisk -l and it only shows the old hard drive.

I have no idea why ubuntu can't see the drive since it shows up in my BIOS and the Windows installer can see it.

I just opened a **[thread ]("http://ubuntuforums.org/showthread.php?t=1011828")**for the same issue 1 hour ago it's a problem with ubiquity and the installer (alternate) it is
already known in lauchpad, but no solution for the moment

---

### Post by logos34 on 2008-12-15
you guys might try running TestDisk from the live cd, maybe it can detect the drive.  The disk should show the correct size and geometry but no partitions (if new in mclane's case).  Then 'write'/save the partition table and try the installer again--maybe then the ubiquity partitioner will recognize it. Worth a shot at least.

On the live cd, do:

>system>admin>software sources>check 'universe' repository

then

sudo apt-get install testdisk

sudo testdisk

Follow these instructions:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Disk_selection](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Disk_selection)

---

### Post by joff13 on 2008-12-15
> **logos34 said:**
> you guys might try running TestDisk from the live cd, maybe it can detect the drive.  The disk should show the correct size and geometry but no partitions (if new in mclane's case).  Then 'write'/save the partition table and try the installer again--maybe then the ubiquity partitioner will recognize it. Worth a shot at least.

On the live cd, do:

>system>admin>software sources>check 'universe' repository

then

sudo apt-get install testdisk

sudo testdisk

Follow these instructions:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Disk_selection](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Disk_selection)

yes worth a shot at least, anyway:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/201286](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/201286)

At the end I think i'll install hardy and then upgrade to intrepid

---

### Post by joff13 on 2008-12-16
> **joff13 said:**
> 
At the end I think i'll install hardy and then upgrade to intrepid

I did, and it worked

---

