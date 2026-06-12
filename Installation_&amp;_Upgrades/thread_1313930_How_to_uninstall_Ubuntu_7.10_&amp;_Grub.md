---
title: "How to uninstall Ubuntu 7.10 &amp; Grub?"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by shivam.seth on 2009-11-04
Hi everyone,

I have been using Ubuntu 7.10 & Windows XP on my Laptop from past two years. Both were loaded in different partitions & worked just fine.

Now, I will be upgrading to a newer laptop & probably will be using latest Ubuntu release too... :D ... but before I do that, I need to uninstall Ubuntu on my old laptop, remove Grub & restore Windows XP on it with its original bootstrap program, i.e. the new user should not be able to find any leftovers from my Ubuntu installation.

How can I do it???... Further, removing Grub & restoring back to Windows bootstrap program is important.

Thanks for any help!

Regards
Shivam

---

### Post by Gorlist on 2009-11-04
Easiest way is to put in the WinXp cd and fix the MBR (Master Boot Record). 

I think if memory serves, your have to press R to enter the recovery console and type "fixmbr" (but search it first). 

As for removing Ubuntu, you just need to delete or format the partition back to NTFS, however to re-extend the original windows is difficult. 

In this case what I would do (and probably just quicker than messing around with the above) is just do a fresh install of windows, deleting all the partitions in the process.

---

### Post by shivam.seth on 2009-11-04
> **Gorlist said:**
> Easiest way is to put in the WinXp cd and fix the MBR (Master Boot Record). 

I think if memory serves, your have to press R to enter the recovery console and type "fixmbr" (but search it first). 

As for removing Ubuntu, you just need to delete or format the partition back to NTFS, however to re-extend the original windows is difficult. 

In this case what I would do (and probably just quicker than messing around with the above) is just do a fresh install of windows, deleting all the partitions in the process.

Thanks buddy for replying!

Actually I have already tried deleting the Ubuntu partition directly but the bootstrap program keeps entries for all the OS installed on the system along with their root addresses. So even after deleting Ubuntu partition, GRUB was throwing an option to boot Ubuntu. Any suggestion for resetting master boot record?

---

### Post by kellemes on 2009-11-04
Couple of methodes you can try..

(copied/pasted from some place..)
```
Boot with the XP installation CD.
When prompted, press R to repair a Windows XP installation.

If repairing a host with multiple operating systems, select the
appropriate one (XP) from the menu. If you have only one operating
system, enter 1 to select it.

Enter the administrator password if prompted.
To fix the MBR, use the following command:
fixmbr

This assumes that your installation is on the C:\ drive. You will be
presented with several scary warning lines the reading of which will make
you want to say no. Microsoft is exceptionally vague regarding the
conditions under which fixmbr can cause problems although they are clear
about the consequences (losing all data on the hard drive), so use this
at your own risk.

Type y and ENTER to fix the MBR.

Type exit to leave the recovery console and reboot.
```


[Same thing but without installation CD]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php") (never tried this one)

And I believe [Super Grub Disk]("http://www.supergrubdisk.org/") also has an option to fix it all..

---

