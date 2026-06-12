---
title: "New HDD Does Not Stay Mounted"
date: 2008-11-08
forum: General Help
---

### Post by BoneSmash on 2008-11-08
I installed a new Seagate 500GB HDD today and everything works fine, but one thing that is really annoying is that it doesn't stay mounted after I reboot or log out.  I have all of my music and videos on this HDD and it's really annoying to have to manually browse to it each time I start up my computer so that Banshee can recognize the HDD.  Is there a way to make it show up automatically, and not as removable media (its icon shows up on my desktop like it would if I had put in a CD)?

---

### Post by taurus on 2008-11-09
Did you add an entry in /etc/fstab to have it mount automatically each time you boot Ubuntu?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by BoneSmash on 2008-11-09
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c060c05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29295   235312056   83  Linux
/dev/sda2           29296       30515     9799650    5  Extended
/dev/sda5           29296       30515     9799618+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003f30b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

---

### Post by taurus on 2008-11-09
I guess you want to mount /dev/sdb1.  Open a terminal and edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   0
```
Save it and close gedit editing window.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
Now, if you want to write to it anytime you want without using sudo, then you can change the ownership if /media/sdb1 from root to your login name.  Assuming your login name is bone, run

```
sudo chown -R bone:bone /media/sdb1
ls -la /media/sdb1
```
You can reboot if you wish and your /dev/sdb1 should be mounted to /media/sdb1.

---

### Post by anystupidname on 2008-11-09
I'm guessing you have not added the appropriate line to your /etc/fstab

/dev/sdb1     /<whereIusuallyMOUNTit>    ext3    default   0   1

I recommend you go the extra mile and do "vol_id /dev/sdb1" to obtain that drive's UUID and use the following line instead

UUID=<whatUjustFOUND>     /<whereIusuallyMOUNTit>    ext3    default   0   1

(please observe the spaces/tabs carefully)

DOH, sorry taurus, double post...

---

### Post by Andreas1 on 2008-11-09
> **taurus said:**
> I guess you want to mount /dev/sdb1.  Open a terminal and edit /etc/fstab
```
/dev/sdb1   /media/sdb1   ext3   defaults   0   0
```

maybe it should be mentioned: if your drive is formatted with ntfs or fat, you must replace "ext3" with "ntfs" or "vfat"

---

### Post by anystupidname on 2008-11-09
> **Andreas1 said:**
> maybe it should be mentioned: if your drive is formatted with ntfs or fat, you must replace "ext3" with "ntfs" or "vfat"

Hi Andreas,

Do you see this in Bonesmash's second post?

> Device Boot Start End Blocks Id System
/dev/sdb1 1 60801 488384001 83 Linux

The partition ID type "83" indicates ext2, 3, 4.
[http://www.osdever.net/documents/pdf/partitiontypes.pdf](http://www.osdever.net/documents/pdf/partitiontypes.pdf)
(NTFS is "07")

---

### Post by taurus on 2008-11-09
> **anystupidname said:**
> Hi Andreas,

Do you see this in Bonesmash's second post?

The partition ID type "83" indicates ext2, 3, 4 or swap.
[http://www.osdever.net/documents/pdf/partitiontypes.pdf](http://www.osdever.net/documents/pdf/partitiontypes.pdf)
(NTFS is "07")

Sorry but ID type 82 is for Linux swap, not 83.

---

### Post by anystupidname on 2008-11-10
Quite right. The ole' memory isn't so great anymore. That's why I backed up the statement with the list heh.:)

---

