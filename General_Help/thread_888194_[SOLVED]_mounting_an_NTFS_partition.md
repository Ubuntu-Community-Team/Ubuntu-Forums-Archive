---
title: "[SOLVED] mounting an NTFS partition"
date: 2008-08-12
forum: General Help
---

### Post by want2bdifferent on 2008-08-12
Hey there

Can anyone tell me how to mount an NTFS Partition?

whenever i click on the volume it says cannot mount volume

sudo fdisk -l comes up with:


Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x099b099b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              12        1765    14089005   83  Linux
/dev/sda2   *        1766        2339     4610655    7  HPFS/NTFS
/dev/sda3            2340        2432      747022+   5  Extended
/dev/sda5            2340        2432      746991   82  Linux swap / Solaris


Thanks in advance :)

---

### Post by pluviosity on 2008-08-12
Have you tried mounting via command line?  If so, try substituting ntfs-3g for mount when you mount the partition.

---

### Post by wd5gnr on 2008-08-12
Open a shell prompt and try:

sudo mount -t ntfs-3g /dev/sda2 /mnt

---

### Post by iaculallad on 2008-08-12
Include the line of text below on the last part of your /etc/fstab file:

> /dev/sda2 /media/NTFS_Drive     ntfs    defaults,umask=007,gid=46 0 

Create the Mount point:

sudo mkdir /media/NTFS_Drive

To do this, edit your fstab file:

```
gksudo gedit /etc/fstab
```

and insert the line of text below. Save and Close.

```
sudo mount -a
```

---

### Post by want2bdifferent on 2008-08-17
> **iaculallad said:**
> Include the line of text below on the last part of your /etc/fstab file:



Create the Mount point:

sudo mkdir /media/NTFS_Drive

To do this, edit your fstab file:

```
gksudo gedit /etc/fstab
```

and insert the line of text below. Save and Close.

```
sudo mount -a
```

How do include that first thing in the file?

 I have not been on here for a while cos i have been busy with school
bear in mind i am new to ubuntu

---

### Post by want2bdifferent on 2008-08-18
> **iaculallad said:**
> Include the line of text below on the last part of your /etc/fstab file:



Create the Mount point:

sudo mkdir /media/NTFS_Drive

To do this, edit your fstab file:

```
gksudo gedit /etc/fstab
```

and insert the line of text below. Save and Close.

```
sudo mount -a
```
ok i did this after i figured out how to so thanks but now it is saying that i do not have the permission to mount this volume

---

### Post by want2bdifferent on 2008-08-18
> **wd5gnr said:**
> Open a shell prompt and try:

sudo mount -t ntfs-3g /dev/sda2 /mnt
ok this is working but i have to log into my windows partition restart it cos i hibernated it.

---

### Post by lordrick112 on 2008-08-18
Also try the NTFS Configuration tool thats under Add/Remove-System.
All I had to do was name my xp partition and voila!!

---

### Post by want2bdifferent on 2008-08-18
> **lordrick112 said:**
> Also try the NTFS Configuration tool thats under Add/Remove-System.
All I had to do was name my xp partition and voila!!
I just tried that and it said:
Mounting /media/NTFS_Drive failed.

fuse: failed to access mountpoint /media/NTFS_Drive: No such file or directory

---

### Post by mb_webguy on 2008-08-18
Ditto lordrick112.  Type "sudo apt-get install ntfs-config" in the terminal, then look for the "Mount NTFS Volumes" program in your Applications menu.  (I think it shows up in either Other or System Tools, but I moved it to System->Administration so I'm not sure.)

The ntfs-config utility mounts the NTFS volume and adds an entry to fstab for you.  If you want special options like adding a umask, uid, or gid, you still need to edit fstab, but at least the tricky part will have already been done for you.

---

### Post by want2bdifferent on 2008-08-19
> **mb_webguy said:**
> Ditto lordrick112.  Type "sudo apt-get install ntfs-config" in the terminal, then look for the "Mount NTFS Volumes" program in your Applications menu.  (I think it shows up in either Other or System Tools, but I moved it to System->Administration so I'm not sure.)

The ntfs-config utility mounts the NTFS volume and adds an entry to fstab for you.  If you want special options like adding a umask, uid, or gid, you still need to edit fstab, but at least the tricky part will have already been done for you.
this is not working.

---

### Post by thestig_992 on 2008-08-19
> **want2bdifferent said:**
> I just tried that and it said:
Mounting /media/NTFS_Drive failed.

fuse: failed to access mountpoint /media/NTFS_Drive: No such file or directory

you mustnt have created the folder properly...remember that ubuntu is case sensitive, so NTFS_Drive is different to ntfs_drive...

if you dont think that you made the folder properly, heres the code again...
```
cd /media
sudo mkdir NTFS_Drive
```

you can change the NTFS_Drive to any name you want, but youll have to modify all of the previous steps that people have told you to take

---

### Post by want2bdifferent on 2008-08-19
> **thestig_992 said:**
> you mustnt have created the folder properly...remember that ubuntu is case sensitive, so NTFS_Drive is different to ntfs_drive...

if you dont think that you made the folder properly, heres the code again...
```
cd /media
sudo mkdir NTFS_Drive
```

you can change the NTFS_Drive to any name you want, but youll have to modify all of the previous steps that people have told you to take
I have done this  but it still says that i am not privilged to mount this volume, i am thinking of getting rid of windows anyway.

---

### Post by want2bdifferent on 2008-08-19
Ok I have been able to mount the drive (thanks :)) however I can not access the files, it tells me that i do not have permission to view the files in this drive.
Thanks in advance:)

---

### Post by want2bdifferent on 2008-08-19
> **want2bdifferent said:**
> Ok I have been able to mount the drive (thanks :)) however I can not access the files, it tells me that i do not have permission to view the files in this drive.
Thanks in advance:)
actually ignore that last message i can now see it, and all my files

thanks a bunch eveyone

---

### Post by vampur on 2008-08-22
Dear 

i am hanged up with this point ?????

as i installed the Ubuntu 8.4 dere si a prb dat i can't not view n switch to the xp files n os.


and i tried many sevral things just to get the data of dat xp and my sudo fdisk -l output is dis ...


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c112c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9729    62790052+   f  W95 Ext'd (LBA)
/dev/sda5            1913        5736    30716248+   b  W95 FAT32
/dev/sda6            5737        7011    10241406    b  W95 FAT32
/dev/sda7            7012        8469    11711353+   b  W95 FAT32
/dev/sda8            8470        9669     9638968+  83  Linux
/dev/sda9            9670        9729      481918+  82  Linux swap / Solaris


Please help me out 

Thankx

---

