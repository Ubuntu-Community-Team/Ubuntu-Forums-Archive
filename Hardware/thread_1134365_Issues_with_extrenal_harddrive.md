---
title: "Issues with extrenal harddrive"
date: 2009-04-23
forum: Hardware
---

### Post by RebelsAreWe on 2009-04-23
I have had a 320 gig external harddrive for quite some time and I had 18 gigs worth of movies and songs on it leaving me the other 300 gigs to add stuff later, of course.

Now recently (and I assume it was something I did, probably not unmounting the external before I unplugged it) it's showing up as a  2 drives, one labeled DRV4_VOL1 as it always has, but that drive only has 18.3 gigs of space on it and the second drive is labeled "disk" and has the other 296.5 gigs on it and I can't add anything to it because it says I'm not the owner. 

If I plug the hdd into a Windows computer it only shows up as the 18.3 and nothing else.

What I want to do is to combine them back into the original 320 gig hdd I used to have. Is this possible or am I going to need to buy a new external?

---

### Post by drs305 on 2009-04-23
First, try mounting it back in Windows again and see if a clean shutdown helps (if that's not what you already did).

Running this command will give us a clearer picture of the device structure. It will show us the partitions and format:
```

sudo fdisk -l  # Note lowercase L

```

Once we confirm what you have, one option would be to run gparted (System, Admin, Partition editor) and just expanding the data files out if there isn't anything else on the drive.

The permission problem is easily fixed with a couple of commands once we see the results of fdisk.

---

### Post by khelben1979 on 2009-04-23
In my opinion you should check how your harddrive has been partitioned using a good partitioning program. [Check this out]("http://en.wikipedia.org/wiki/List_of_disk_partitioning_software") for more information.

---

### Post by RebelsAreWe on 2009-04-23
> **drs305 said:**
> First, try mounting it back in Windows again and see if a clean shutdown helps (if that's not what you already did).

Running this command will give us a clearer picture of the device structure. It will show us the partitions and format:
```

sudo fdisk -l  # Note lowercase L

```Once we confirm what you have, one option would be to run gparted (System, Admin, Partition editor) and just expanding the data files out if there isn't anything else on the drive.

The permission problem is easily fixed with a couple of commands once we see the results of fdisk.


Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf47bf47b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10b006fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2389    19189611    c  W95 FAT32 (LBA)
/dev/sdc2            2390       38913   293379030    5  Extended
/dev/sdc5            2390       38442   289595691   83  Linux
/dev/sdc6           38443       38913     3783276   82  Linux swap / Solaris

---

### Post by drs305 on 2009-04-23
I dont' see anything wrong with /dev/sdc, so try mounting it after making a mount point and let's see if both partitions will mount, even if there isn't anything in it.

```

sudo mkdir /media/sdc5
sudo chown -R *yourusername:* /media/sdc5   # Example: sudo chown -R john: /media/sdc5
mount /dev/sdc5 /media/sdc5

```
If there are no errors, the partition should be mounted on /media/sdc5 and you should be able to add/delete files.

If that works, then you aren't having any problems with the drive and partition table. If you wish to create one large partition, proceed with:

```

sudo umount /dev/sdc5
gksudo gparted /dev/sdc

```
You should be able to delete the sdc5 partition. 
Next delete the sdc2 extended partition.
Finally, expand your sdc1 partition.

Personally, I like extended partitions, but if you don't plan on having more than 4 partitions the above is a way to do what you want.

Of course, any partitioning involves the risk of data loss, so if you can back up your data before performing this operation I highly recommend it.
This will open up the partition editor.

---

### Post by RebelsAreWe on 2009-04-23
I followed step by step the instructions you gave me and I'm getting

mount: can't find /dev/sdc5/media/sdc5 in /etc/fstab or /etc/mtab

No other errors

---

### Post by RebelsAreWe on 2009-04-23
ok I got it to mount but it only mounted the 296.5 gigs, not the whole 320

---

### Post by drs305 on 2009-04-23
> **RebelsAreWe said:**
> ok I got it to mount but it only mounted the 296.5 gigs, not the whole 320

That is what it was doing. It only mounted sdc5. But we now know that the partition structures are ok. You can either leave it the way it is, with two partitions (your other partition should be mounted on DRV4_VOL1).

Confirming there wasn't anything on sdc5 when you mounted it and that you want to merge the two partitions, follow the second part of my previous post. 

You will unmount sdc5, open gparted, delete sdc5, then sdc2, then expand sdc1. I guess you want to keep it as NTFS?

If that is the case, once you have one partiion, install and run the following. This will install two apps used with NTFS partitions:
```
sudo apt-get install ntfs-config  ntfsprogs
gksudo ntfs-config

```
The second command will open up an app that will let you automatically mount the drive at boot. You will tell the app to enable write support, then pick a mount point. The mount point will be under /media, so if you want /media/mydata, you would type in *mydata*. If you want to open the app via a menu, it's located under Applications, System Tools.

It will make an entry in /etc/fstab and the partition will mount on boot.

---

