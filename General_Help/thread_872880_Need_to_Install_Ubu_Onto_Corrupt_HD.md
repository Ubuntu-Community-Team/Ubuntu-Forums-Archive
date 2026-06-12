---
title: "Need to Install Ubu Onto Corrupt HD"
date: 2008-07-28
forum: General Help
---

### Post by hkelley on 2008-07-28
I am attempting to install Ubuntu on to a laptop HD that is corrupt. I need a method of formatting the HD before I install Ubuntu but I do not have the orig Windows XP disks. I am unable to get to a command line so I can run chkdsk /f. Is there a simple method of reformatting this HD before attempting an Unbuntu install?

---

### Post by Shazaam on 2008-07-28
Are you going to wipe the drive and start over or are you trying to repair a Windows install?
Boot the Ubuntu livecd and start gparted (System>Administration>Partition Editor). You can format the drive/partitions there.

---

### Post by hkelley on 2008-07-28
My objective is a fresh format/fresh Ubuntu install. When I attempt to run Ubuntu from the CD it hangs after a a couple of passes of the loading bar consequently I can't get to the system admin. However, I am successful in running Knoppix from the CD as well as Puppy Linux.

---

### Post by lordadi on 2008-07-28
Hi,

If you are looking for a wipe of the hard disk and just Ubuntu on it, you should be able to use the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php").



Cheers,

Lordadi.

---

### Post by zvacet on 2008-07-28
> My objective is a fresh format/fresh Ubuntu install.

Use manual way of partition and there erase all partitions and make new ones.

---

### Post by hkelley on 2008-07-29
The suggestion of using GParted CD Live has gained some progress, however, I am still unable to load Ubuntu or Xubuntu. I am getting an MBR 1 Error after I attempt to reboot without the CD in place. Both Ubuntu and Xubunto lock up during the install process. Can GPartCD corrected MBR error?

---

### Post by lordadi on 2008-07-29
Hi,

If you are just wiping your disk then the LiveCD should be able to help as it will boot like a Linux CD. Since you are looking for a fresh Ubuntu install (NO windows whatsoever) then the MBR too will be wiped as it is a windows bootloader.

Sorry, I dont know if GParted will correct MBR issues.

Cheers,


Lordadi.

---

### Post by Shazaam on 2008-07-29
> **hkelley said:**
> My objective is a fresh format/fresh Ubuntu install. When I attempt to run Ubuntu from the CD it hangs after a a couple of passes of the loading bar consequently I can't get to the system admin. However, I am successful in running Knoppix from the CD as well as Puppy Linux.

You can use Qtparted on the Knoppix cd to format the hard drive too. It has a different layout than gparted but the results will be the same.

---

