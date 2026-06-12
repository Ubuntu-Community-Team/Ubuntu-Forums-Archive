---
title: "Harddrive Read Write and Fstab"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by crhooker on 2006-02-05
I almost have my system where I want it. I just lack some configuration steps. I have certainly read previous posts and tried a few thing on what I saw but none seem to work, it seems to have something to do with adding a harddrive and perhaps changing my motherboard. Anyway...

Here is my system as it sits now:

Dual booting harddrives (info from Gparted)
Maxtor 80GB - master
/dev/hda1 ext3  boot
/devhda2 extended
/dev/hda5 linux-swap

Seagate 300Gb - slave
/dev/hdb1 ntfs (50Gb) - XP booted via GRUB(THANKS to "lha" for that help)
/dev/hdb2 extended
/dev/hdb5 fat32 (250Gb) - I partioned and setup w/ Gparted

Maxtor External 250Gb
/dev/sda1 fat32

I also have two DVD's one is player only the other is RW

the Maxtor80Gb is fine and all is well - so is the Maxtor External 250Gb and the DVD's. The problem is with the Seagate 300Gb.

I formatted it with Gparted but cannot seem to mount it and was wondering if it had anything to do with my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

As I look at this nothing seems to be right.

thanks for help - I cannot trumpet loud enough the great support from this community - I swear as I get better with Ubuntu I will start giving back.

Carl

---

### Post by Sutekh on 2006-02-05
[QUOTE=crhooker]
Here is my system as it sits now:

Dual booting harddrives (info from Gparted)
Maxtor 80GB - master
/dev/hda1 ext3  boot
/devhda2 extended
/dev/hda5 linux-swap

Seagate 300Gb - slave
/dev/hdb1 ntfs (50Gb) - XP booted via GRUB(THANKS to "lha" for that help)
/dev/hdb2 extended
/dev/hdb5 fat32 (250Gb) - I partioned and setup w/ Gparted

Maxtor External 250Gb
/dev/sda1 fat32

I also have two DVD's one is player only the other is RW

the Maxtor80Gb is fine and all is well - so is the Maxtor External 250Gb and the DVD's. The problem is with the Seagate 300Gb.

I formatted it with Gparted but cannot seem to mount it and was wondering if it had anything to do with my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

As I look at this nothing seems to be right.
[/QUOTE]
Is this your whole fstab?  It looks very strange.  Your hda (apparently the Maxtor 80GB) is mounted as a cdrom.  Same with the Seagate.  I agree nothing seems right.

Can you post the output of this command
```
sudo fdisk-l
```
This will list all the information about your partitions.

---

### Post by crhooker on 2006-02-05
[QUOTE=Sutekh]Is this your whole fstab?  It looks very strange.  Your hda (apparently the Maxtor 80GB) is mounted as a cdrom.  Same with the Seagate.  I agree nothing seems right.

Can you post the output of this command
```
sudo fdisk-l
```
This will list all the information about your partitions.[/QUOTE]

when I run in terminal I get 

carl@hooker:~$ sudo fdisk-l
Password:
sudo: fdisk-l: command not found
carl@hooker:~$ sudo fdisk-l
sudo: fdisk-l: command not found
carl@hooker:~$

---

### Post by Sutekh on 2006-02-05
SOrry I have a crappy KVM switch at work and it keeps messing with my typing
There needs to be a space between the fdisk and the -l
```
sudo fdisk -l
```

---

### Post by crhooker on 2006-02-05
[QUOTE=Sutekh]SOrry I have a crappy KVM switch at work and it keeps messing with my typing
There needs to be a space between the fdisk and the -l
```
sudo fdisk -l
```[/QUOTE]


No problem, thanks for helping, here you go

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hdb2            6375       36481   241834477+   5  Extended
/dev/hdb5            6375       36481   241834446    6  FAT16

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

---

### Post by Sutekh on 2006-02-05
[QUOTE=crhooker]
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 9352 75119908+ 83 Linux
/dev/hda2 9353 9729 3028252+ 5 Extended
/dev/hda5 9353 9729 3028221 82 Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 6374 51199123+ 7 HPFS/NTFS
/dev/hdb2 6375 36481 241834477+ 5 Extended
/dev/hdb5 6375 36481 241834446 6 FAT16

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 30401 244196001 c W95 FAT32 (LBA)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

[/QUOTE]
Okay to start the second and third lines should not be hdc1 and hdc5 they should be hda1 and hda5.

So they should look like
```
/dev/hd**a**1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hd**a**5       none            swap    sw              0       0

```

Then the fourth and fifth lines for your DVD drives should not be hda and hdb.  I Imagine they are probably **hdc** and **hdd**.


Now for your other drives (Seagate 300GB - hdb and Maxtor 250GB - sda)

This link has a really good explanation for mounting Windows partitions NTFS and FAT)
[Mounting Windows in Ubuntu - by ]("http://www.psychocats.net/linux/mountwindows.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

Have a read, but to summarise, to mount your Windows NTFS partition (**hdb1**) , I'd use the line
```

/dev/**hdb1** [COLOR="Red"]/windows[/COLOR] ntfs nls=utf8,umask=0222 0 0
```
The red text - /windows is the folder wher the NTFS partition would be mounted to.  YOu can change this to anything you like, just make sure that you create the folder first.  If you wanted to use /windows, then create the folder
```
sudo mkdir /windows
```

To mount the first FAT32 partition (**hdb5**), I'd use the line
```
/dev/**hdb5** [COLOR="Red"]/fat_files1[/COLOR] vfat iocharset=utf8,umask=000 0 0

```
Again the red text - /fat_files1 refers to the folder where this partition would be mounted.  You may change it to anything you like, just ensure that the folder exists.

TO mount the second FAT32 partition (**sda1** on theMaxtor 25GB), I'd use the line
```

/dev/**sda1** [COLOR="Red"]/fat_files2[/COLOR] vfat iocharset=utf8,umask=000 0 0

```
Again the red text - fat_files2 may be changed to whatever you would like to call the mount folder for this FAT32 partition.


So I'd probably have a /etc/fstab that has these lines
```

proc            /proc           proc    defaults        0       0

/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0

/dev/hdb1       /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb5       /fat_files1 vfat iocharset=utf8,umask=000 0 0

/dev/sda1       /fat_files2 vfat iocharset=utf8,umask=000 0 0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```


I would also suggest that you mke sure you udnersatnd all that I've said before trying anything first.

---

### Post by crhooker on 2006-02-05
[QUOTE=Sutekh]
So I'd probably have a /etc/fstab that has these lines
```

proc            /proc           proc    defaults        0       0

/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0

/dev/hdb1       /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb5       /fat_files1 vfat iocharset=utf8,umask=000 0 0

/dev/sda1       /fat_files2 vfat iocharset=utf8,umask=000 0 0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```


I would also suggest that you mke sure you udnersatnd all that I've said before trying anything first.[/QUOTE]

Thanks, I will give it a look and read the link. If you do not mind I will repost what I think I should make fstab after I understand as you suggest with the names I have chosen.

Also - why does the hdb5 read as fat16 when GParted shows it as fat32?

carl

---

### Post by Sutekh on 2006-02-05
[QUOTE=crhooker]Thanks, I will give it a look and read the link. If you do not mind I will repost what I think I should make fstab after I understand as you suggest with the names I have chosen.

Also - why does the hdb5 read as fat16 when GParted shows it as fat32?

carl[/QUOTE]
That sounds good to me.

I'm not sure why hdb5 looks like FAT16, especially since you used GParted to create it.

---

