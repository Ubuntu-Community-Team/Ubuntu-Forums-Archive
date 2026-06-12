---
title: "Partition Hard drive"
date: 2008-07-30
forum: General Help
---

### Post by Maccer101 on 2008-07-30
Hi,

Am in the process of putting together a new build, and will install Hardy Heron 8.04 on it.

However as this PC will be networked to my primary machine running Vista via a Router I want to partition the 250gb hard drive so I have a 150-200gb NTFS formatted partition as well as the Ubuntu partiton so I can easily file share and back up data files between the 2 PCs.

Hardy Heron 8.04 will read NTFS (have tested running it from the  install CD and opened windows files)but am not sure how I should go about the process of doing this.

Should I install Ubuntu firt then create the NTFS partition? or should I partition the HDD first before installing an OS, but how would I do this?

This is my first build and first time using Ubuntu so any help would be greatly appreciated.

really want to use NTFS instead of Fat32 due to Fat32 limitations.

many thanks

---

### Post by coffeecat on 2008-07-30
> **Maccer101 said:**
> Should I install Ubuntu firt then create the NTFS partition? or should I partition the HDD first before installing an OS, but how would I do this?

If you go to System > Administration > Partition Editor in the live CD environment, you get Gparted. So you could partition up your hard drive, not just with the NTFS partition you want, but the partitions you need for your Ubuntu install, plus any others you might want. Then, go to the installer and choose the custom option (I think it is) at the partitioning stage to install onto your pre-prepared partitions.

You'll need to choose something other than the first choice at the partitioning stage in the installer anyway, otherwise it will use your whole disc.

I use NTFS for data sharing between Windows and Ubuntu. One tip: have a look at ntfsprogs, a whole suite of ntfs tools in Linux. I can't remember whether it's in a default install, but easily installed with Synaptic if not. You can label NTFS partitions with one of the tools (can't remember which and I'm using Mac OS atm so I can't check). This is useful, because the mounted partition icon will have the partition label rather than some generic name.

**Edit:** I just noticed that you said 'Ubuntu partition' (in the singular). As you are a first-time poster, I don't know how much Ubuntu/Linux experience you have. Are you aware that, as a minimum, you need two partitions - one root (/) and one swap? Some people like a separate /home. Post back if you need any more information.

---

### Post by Rocket2DMn on 2008-07-30
I would partition the hard drive first, it makes it easier after the install because the partitions should be automatically detected by Ubuntu during install.  You can partition from the LiveCD using System->Administration->Partition Editor
I suggest you make backups for your important data before resizing and repartitioning.  It is possible for something to go wrong, though it is more likely that you will screw something up rather than the partitioner going bad.  If you are resizing a windows partition, don't forget to defragment it first.

The screenshots on this page are a little old I think, but the basics are the same - [uhelp]community/HowtoPartition[/uhelp]

---

### Post by drs305 on 2008-07-30
from coffeecat's post:

Once you have ubuntu installed:

```
sudo aptitude install ntfsprogs
```

The command for labeling ntfs partitions is:
```

sudo ntfslabel <device> <label>

```
Example: sudo ntfslabel /dev/sda5 MYLABEL

Then don't forget there is also an NTFS configuration tool:
System Tools, NTFS Configuration Tool

You can also set up your ntfs partition in fstab using a gui-based fstab editor. See the link below.

---

### Post by Rocket2DMn on 2008-07-30
For more help with labeling drives and moving mount points see
[uhelp]community/MoveMountpointHowto[/uhelp]
[uhelp]community/RenameUSBDrive[/uhelp]
-the latter can work for internal drives, too, though changing the fstab entry is preferred as well.

---

### Post by bodhi.zazen on 2008-07-30
I do not understand why you want a ntfs partition, IMO unless you are running windows on the box you should stay with linux native partitions. You do not need a ntfs partition to file share, ie you can file share w/ samba, nfs, ftp, http, ssh (scp) all with ext3 or any other linux native file system.

At any rate, boot the live CD use gparted to make partitions, then install.

gparted Documentation: [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by hessiess on 2008-07-30
dont use NTFS, it fragments verry easely and as far as i know there is no way to defrag NTFS in Linux.

---

