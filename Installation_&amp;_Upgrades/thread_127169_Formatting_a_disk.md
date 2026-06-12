---
title: "Formatting a disk"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by Hanj on 2006-02-08
I'm setting up a computer to act as a file server (running Breezy). The machine has two disks, one 80 GB and one 200 GB, and used to have Windows on the 80 disk and Ubuntu on the 200. Now I have installed a server system and I picked "erase entire disk" for the 80 GB disk, so the other disk still contains my old linux file system. 'fdisk -l' gives the following output:
```

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9777    78533721   83  Linux
/dev/hda2            9778        9964     1502077+   5  Extended
/dev/hda5            9778        9964     1502046   82  Linux swap / Solaris

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       24133   193848291   83  Linux
/dev/hdc2           24134       24321     1510110    5  Extended
/dev/hdc5           24134       24321     1510078+  82  Linux swap / Solaris

```

I want to wipe out everything on /dev/hdc and then mount it and share it using Samba. The problem is that I have never used fdisk and I don't really understand the man pages well enough. So I was wondering if someone could give me some hints on how to clear the entire disk, or maybe point me to some partitioning program that is easier to use (it has to be text-mode only). 

I'm afraid to mess things up if I start experimenting with fdisk, and I couldn't find anything helpful on these forums.

---

### Post by wrtrdood on 2006-02-08
Using *fdisk* is not as difficult as it may seem but it does require a bit of experience.  Use *cfdisk* instead.  It will give you a nice menu driven style tool which you should find less intimidating.  If I understand what you're saying, you want to make /dev/hdc a single partition.  Not a problem.  First, delete all the **hdc** partitions shown then add one back that covers the entire drive.  When this step is completed you'll need to use one of the *mkfs* tools to create the filesystem (check man mkfs).  After that, simply create a mount point and mount /dev/hdc1.  Don't forget to update /etc/fstab to make it permanent.

---

### Post by Hanj on 2006-02-08
Thanks alot, wrtrdood, cfdisk was just what I was looking for. Everything seems to have worked fine.

---

