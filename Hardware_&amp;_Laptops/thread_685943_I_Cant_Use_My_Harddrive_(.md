---
title: "I Cant Use My Harddrive :("
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by iiDopDop!! on 2008-02-02
i have an 80 gig HDD that i want to put music on because my main drive is getting full. but i cant do anything with the drive besides mount it, it has one folder in it called "Lost+Found" and when i open it, it says i dont have the correct permissions to read the contents. All the permissions are on "root" how do i change it so i can use the harddrive?

---

### Post by tonyric on 2008-02-02
> **iiDopDop!! said:**
> i have an 80 gig HDD that i want to put music on because my main drive is getting full. but i cant do anything with the drive besides mount it, it has one folder in it called "Lost+Found" and when i open it, it says i dont have the correct permissions to read the contents. All the permissions are on "root" how do i change it so i can use the harddrive?

Try using 'sudo chmod 777 <path>' or 'sudo chown <userid> <path>'

---

### Post by Ocxic on 2008-02-02
```

sudo chown your-user:your-user /path/to/mount/point

ex: sudo chown ocxic:ocxic /media/harddrive1

```

---

### Post by Yellow Pasque on 2008-02-02
The best way to fix it would be to modify the entry of the disk in your /etc/fstab file, so please post that file.

---

### Post by hgrizzle on 2008-02-03
Okay, so I didn't start this thread, but I have the same problem and I thought maybe I could get some help here. First off, I have one 80gb harddrive that ubuntu 7.10 is installed on and it works fine. I have a second hard drive that I can navigate to and it has a lost + found folder in it, but I cannot open it or add files to it. I want to use it to save music and video on. I posted my /etc/fstab file below. Thanks, in advance for any help.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7d4e6a9c-2907-4feb-acbb-2b5e3df4ae68 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a5fe9d6e-7815-4bce-a629-fca084c4f33c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Yellow Pasque on 2008-02-03
OK, hgrizzle, can you post the result of the following commands so we can see how yopur disk is layed out?
```
sudo fdisk -l
sudo lshw -businfo -C disk
```

---

### Post by hgrizzle on 2008-02-03
Here are the results from the two commands

**sudo fdisk -l**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b1560

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9447    75882996   83  Linux
/dev/sda2            9448        9729     2265165    5  Extended
/dev/sda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa863a863

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

**and sudo lshw businfo -C disk**

Bus info          Device      Class       Description
=====================================================
scsi@0:0.0.0      /dev/sda    disk        74GB WDC WD800BB-53DK
scsi@0:0.1.0      /dev/sdb    disk        74GB WDC WD800BB-53CA
scsi@1:0.0.0      /dev/cdrom  disk        CD-ROM LTN486S
heath@heath-desktop:~$

---

### Post by Yellow Pasque on 2008-02-03
Do you know what directory you want to mount to? (probably /media/disk)
If not, make the directory:
```
cd /media
sudo mkdir disk
sudo gedit /etc/fstab
```

Then, it should just be a matter of adding this line:
```
/dev/sdb1  /media/disk  ext3  rw,auto,exec,user,uid=1000  0  0
```

---

### Post by iiDopDop!! on 2008-02-03
i dont mean to offend anyone hear... but me trying to understand some of those posts was like me trying to read japanese.... i dont know where to start. But i did what you told the other guy to do here is my results.

sudo fdisk -l :

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5feb5fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9447    75882996   83  Linux
/dev/sda2            9448        9729     2265165    5  Extended
/dev/sda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc07fc07f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+  83  Lin{ux

{and.....}

sudo lshw -businfo -C disk

Bus info          Device       Class       Description
======================================================
scsi@0:0.0.0      /dev/sda     disk        74GB ST380011A
scsi@0:0.1.0      /dev/sdb     disk        74GB ST380011A
scsi@1:0.0.0      /dev/cdrom1  disk        DVD-ROM
scsi@1:0.1.0      /dev/cdrom   disk        LTR-52327S

theres what i got... to me it looks like the problems fixed if i follow what you told the other guy to do?? is that right?

---

### Post by Yellow Pasque on 2008-02-03
> theres what i got... to me it looks like the problems fixed if i follow what you told the other guy to do?? is that right?
It should. Let me know if you have any issues.

---

### Post by hgrizzle on 2008-02-03
I assume I'll need to restart it for the settings to take effect? I've got something downloading right now, so I'll give an update as to whether it worked or not in an hour or so when the download is finished.

Thanks for your help so far.

---

### Post by Yellow Pasque on 2008-02-03
Yeah, for the fstab entry to take effect, you must restart. You could also try mounting it now manually.
```

sudo mount -t ext3 -o rw,user,auto,exec,uid=1000 /dev/sdb1 /media/disk
```

---

### Post by hgrizzle on 2008-02-04
Okay, so I've tried what you suggested (modifying the file in sudo gedit /etc/fstab) and it doesn't seem to be working. Now in addition to my working drives I see 74.5 GB volume and disk (both are the second harddrive) but when I click on them it says unable to mount. Do you guys have any more ideas?

---

### Post by Yellow Pasque on 2008-02-04
My apologies, I gave you a bad option. Take out the uid=1000 from the fstab entry.

---

### Post by hgrizzle on 2008-02-04
I removed uid=1000 but I still have the same problem. Unable to mount.

---

### Post by iiDopDop!! on 2008-02-07
hey ti didnt work for me either now i cant see the harddrive at all.... it doesnt show up for me to be able to mount it and i got the unable to mount error and once i removed the uid=1000 it didnt show up at all.... im confused again lol

---

### Post by hgrizzle on 2008-02-07
Well at least I'm not the only one. I was feeling stupid.

---

### Post by cdtech on 2008-02-08
> **iiDopDop!! said:**
> i have an 80 gig HDD that i want to put music on because my main drive is getting full. but i cant do anything with the drive besides mount it, it has one folder in it called "Lost+Found" and when i open it, it says i dont have the correct permissions to read the contents. All the permissions are on "root" how do i change it so i can use the harddrive?

You don't use that directory. Add a folder and call it music or whatever and store your music in that folder. You said you can mount and see the folder so theres nothing wrong with what your doing.

You must have formated that drive with ext3 to have a lost and found folder. Just start filling it up with music (the music folder you create). Once you create a folder it will have the proper permissions.

---

### Post by ROOP on 2008-02-17
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x039a039a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9824    78911248+  83  Linux
/dev/sda2            9825       10011     1502077+   5  Extended
/dev/sda5            9825       10011     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02500250

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux
```

```

Bus info          Device       Class       Description
======================================================
scsi@0:0.0.0      /dev/sda     disk        76GB HDS722580VLAT20
scsi@0:0.1.0      /dev/sdb     disk        111GB WDC WD1200BB-00D
scsi@1:0.0.0      /dev/cdrom   disk        CD-ROM Max 50X
scsi@1:0.1.0      /dev/cdrom1  disk        NR-7700A
```

```
cd /media
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: /dev/sdb1 already mounted or /media/sdb1 busy
sudo umount -t ext3 /dev/sdb1 /media/sdb1
umount: /dev/sdb1: not mounted
umount: /media/sdb1: not mounted
```

/dev/sdb1 is what im trying to mount, ever since upgrade to gutsy gibbon. I cant mount the drive. I see the drive on my computer:/// along with other HDD, and CD-ROMs. Just will not mount but says mounted.

---

### Post by Yellow Pasque on 2008-02-17
ROOP, post your /etc/fstab

---

### Post by ROOP on 2008-02-17
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=de2f9c2b-78d0-4583-bbff-9b1685bf6d84 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=2134d840-0d4e-43a9-b1cb-c0c8151d2376 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by Yellow Pasque on 2008-02-17
OK, try adding a line like the following:
```
/dev/sdb1 <directory where you want to mount>  ext3  rw,auto,exec,user  0  0
```
If you don't know what <directory where you want to mount> is, try mounting to /media/disk.
Just make sure /media/disk exists and you have permissions for it, so:
```
cd /media
sudo mkdir disk
chmod 777 disk
```

---

### Post by ROOP on 2008-02-17
> **Temüjin said:**
> OK, try adding a line like the following:
```
/dev/sdb1 <directory where you want to mount>  ext3  rw,auto,exec,user  0  0
```
If you don't know what <directory where you want to mount> is, try mounting to /media/disk.
Just make sure /media/disk exists and you have permissions for it, so:
```
cd /media
sudo mkdir disk
chmod 777 disk
```




```
chmod 777 disk
chmod: changing permissions of `disk': Operation not permitted
```

```
dev/sdb1 /media/disk  ext3  rw,auto,exec,user  0  0
```


I added the new line to /etc/fstab don't see it mounted, to the mount point /media/disk. Do I need to restart?

---

### Post by Yellow Pasque on 2008-02-17
Yes, you'll need to restart for the changes in /etc/fstab to take effect. Before you do, let's fix the chmod (sorry that I forgot the 'sudo' in the first post):
```
cd /media
**sudo** chmod 777 disk
```

---

### Post by cdtech on 2008-02-17
just "mount -a" to see the changes.

By using the command line "blkid" you will see your block id for your drives partitions. Using the block id in the fstab would be the failsafe method, like mine is shown here for my sda partition.
```

# /dev/sda1
UUID=1D8FD5F25AC0301F /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

```
Normally /dev/sda# or /dev/hda# is fine in /etc/fstab. However, Ubuntu prefers using the blkid number.

Just my 2 pennies though.

---

### Post by ROOP on 2008-02-18
> **Temüjin said:**
> Yes, you'll need to restart for the changes in /etc/fstab to take effect. Before you do, let's fix the chmod (sorry that I forgot the 'sudo' in the first post):
```
cd /media
**sudo** chmod 777 disk
```

Still no dice. changed chmod, and added new line. Still not mounted. What should the etc/fstab look like when I add the new line. Do I just add it to the bottom? Starting to get a little lost now. Wish I never upgraded to Gutsy, with this problem. lol. Hard one to work out.

---

### Post by cdtech on 2008-02-18
> **ROOP said:**
> Still no dice. changed chmod, and added new line. Still not mounted. What should the etc/fstab look like when I add the new line. Do I just add it to the bottom? Starting to get a little lost now. Wish I never upgraded to Gutsy, with this problem. lol. Hard one to work out.

This is what my fstab looks like using the blkid:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb7
UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=96c0de58-1d53-4fc6-8f35-90cb5dbd78ac /boot           ext3    defaults        0       2
# /dev/sdb6
UUID=aed3efe3-53d1-4b88-9c36-c87678436f45 /home           ext3    defaults        0       2
# /dev/sda1
UUID=1D8FD5F25AC0301F /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=C6AAD33AAAD325A9   /media/Storage  ntfs    defaults,umask=007,gid=46 0     1
# /dev/sdb5
UUID=895c93de-63d5-468f-99b7-d0f70696928b        none            swap    sw     0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
blkid:
```
/dev/sda1: UUID="1D8FD5F25AC0301F" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sdb1: UUID="96c0de58-1d53-4fc6-8f35-90cb5dbd78ac" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="895c93de-63d5-468f-99b7-d0f70696928b" 
/dev/sdb6: UUID="aed3efe3-53d1-4b88-9c36-c87678436f45" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="41d95d32-e6bf-418b-b3fe-278d0c7ba5e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="C6AAD33AAAD325A9" LABEL="Storage" TYPE="ntfs"
```
Drives using **sudo lshw -businfo -C disk**
```
Bus info          Device     Class       Description
====================================================
ide@0.0           /dev/hda   disk        PIONEER DVDRW DVR-K17B
                  /dev/hda   disk        
scsi@0:0.0.0      /dev/sda   disk        149GB WDC WD1600BEVS-6
scsi@1:0.0.0      /dev/sdb   disk        232GB WDC WD2500BEVS-6
```
If you already have a device listed in your fstab (your sdb drive) then just change it to look like what you find using these commands or add it like in my fstab using your block id.

**Your sdb is like my sda in the above fstab......Oh My.**
You really don't need to restart for changes, just do a mount -a. This will mount everything in your fstab file.

---

### Post by phenest on 2008-02-18
> **cdtech said:**
> You don't use that directory. Add a folder and call it music or whatever and store your music in that folder. You said you can mount and see the folder so theres nothing wrong with what your doing.

You must have formated that drive with ext3 to have a lost and found folder. Just start filling it up with music (the music folder you create). Once you create a folder it will have the proper permissions.

This is correct. Every partition has a lost+found in its upper directory. Files that were saved during failures are here. Just ignore it.

---

### Post by ROOP on 2008-02-18
This is what i have it as now.

```

sudo lshw -businfo -C disk
Bus info          Device       Class       Description
======================================================
scsi@0:0.0.0      /dev/sda     disk        76GB HDS722580VLAT20
scsi@0:0.1.0      /dev/sdb     disk        111GB WDC WD1200BB-00D
scsi@1:0.0.0      /dev/cdrom   disk        CD-ROM Max 50X
scsi@1:0.1.0      /dev/cdrom1  disk        NR-7700A
scsi@3:0.0.0      /dev/sdc     disk        232GB 2500JB External
```

```
/dev/mapper/sdb1: UUID="9505e93a-a335-4365-9a8e-0473bc93601f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swsuspend" UUID="48da2489-c193-494f-8c39-e89ae341d5cb" 
/dev/sda1: UUID="de2f9c2b-78d0-4583-bbff-9b1685bf6d84" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="ESSENTIAL" UUID="3717-D230" TYPE="vfat" 
/dev/mapper/sda5: TYPE="swsuspend" UUID="48da2489-c193-494f-8c39-e89ae341d5cb" 
/dev/sdb1: UUID="9505e93a-a335-4365-9a8e-0473bc93601f" SEC_TYPE="ext2" TYPE="ext3" 
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=de2f9c2b-78d0-4583-bbff-9b1685bf6d84 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=2134d840-0d4e-43a9-b1cb-c0c8151d2376 none swap sw 0 0
# /dev/sdb1 
UUID=9505e93a-a335-4365-9a8e-0473bc93601f /media/disk  ext3  rw,auto,exec,user  0  0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

```


```
sudo mount -a
mount: /dev/sdb1 already mounted or /media/disk busy
```

---

