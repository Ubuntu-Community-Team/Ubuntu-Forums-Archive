---
title: "Complicated mounting"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by kostaschatzi on 2007-01-25
Hello dear users,

My topic seems a bit cliche to you but i have really read a lot about in this forum and i really don t know where to start and what to do.I have a dual boot system with ubuntu 6.10 and winxp and my windows hard disks need mounting.This is not the difficult part though.The windows hard disk is not only one and doesn t have only one file system.I have two hard drives(one that contains the windows installation) in ntfs file system and also i have another one in fat32 apart from the linux existing ones.I have read some topics about how to mount  them and in fact i even found step by step information how to do this.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

However,since i don t understand the language i would really need someone to tell me step by step what to do.

For your help i will attach the following information

kostas@ubuntuKL:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       27069   155991150    f  W95 Ext'd (LBA)
/dev/sda3           27070       30401    26764290   83  Linux
/dev/sda5            7650       20397   102398278+   b  W95 FAT32
/dev/sda6           20398       26923    52420063+   7  HPFS/NTFS
/dev/sda7           26924       27069     1172713+  82  Linux swap / Solaris

AND

 GNU nano 1.3.12             File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8eb0195a-d164-4eac-838c-b89a5ddbebb9 /               ext3    defaults,erro$
# /dev/sda7
UUID=29227b60-28c4-4979-ae3a-295868576edd none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

I don t know what else to post.I am at your disposal for any other information you might need

Thank you in advance
kostas

---

### Post by Jussi Kukkonen on 2007-01-25
You can find your windows partitions here:
> **/dev/sda1 * 1 7649 61440561 7 HPFS/NTFS**
/dev/sda2 7650 27069 155991150 f W95 Ext'd (LBA)
/dev/sda3 27070 30401 26764290 83 Linux
**/dev/sda5 7650 20397 102398278+ b W95 FAT32**
**/dev/sda6 20398 26923 52420063+ 7 HPFS/NTFS**
/dev/sda7 26924 27069 1172713+ 82 Linux swap / Solaris
2 NTFS-partitions (NTFS is read-only in linux at the moment, at least by default) and one FAT. Let's create directories (you can name them smarter if you want ):
```
sudo mkdir  /media/fat-sda5
sudo mkdir  /media/ntfs-sda1
sudo mkdir  /media/ntfs-sda6

```
then edit your fstab (take a backup first) with ***sudo nano /etc/fstab***:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=8eb0195a-d164-4eac-838c-b89a5ddbebb9 / ext3 defaults,erro$
# /dev/sda7
UUID=29227b60-28c4-4979-ae3a-295868576edd none swap sw $
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

## added windows partitions:
/dev/sda5 /media/fat-sda5 vfat iocharset=utf8,umask=000 0 0
/dev/sda1 /media/ntfs-sda1 ntfs nls=utf8,umask=0222 0 0
/dev/sda6 /media/ntfs-sda6 ntfs nls=utf8,umask=0222 0 0

```
then remount:
```
sudo mount -a
```

---

### Post by Jussi Kukkonen on 2007-01-25
More information (possibly confusing, sorry about that) here: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Especially useful if you want read-access to ntfs.

---

### Post by kostaschatzi on 2007-01-25
Thank you for your help guys...

i would like to state something to Jussi Kukkonen.
You tell me to create new directories in the /media file.I inform you that in the webpage i was advised to create a /windows directory.Should i create these directories inside there or is it completely irrelative?

kostas

---

### Post by meng on 2007-01-25
It's whatever you prefer.
If you put it within /media, it will show up as an icon on your desktop when it is mounted.

---

### Post by logos34 on 2007-01-25
> I have a dual boot system with ubuntu 6.10 and winxp and my windows hard disks need mounting.This is not the difficult part though.The windows hard disk is not only one and doesn t have only one file system.I have **two hard drives**(one that contains the windows installation) in ntfs file system and also i have another one in fat32 apart from the linux existing ones.

Do you mean 'partitions' when you say 'drives'?  Or do you have other hard disks in addition to the 250gb sata that's showing up?

---

### Post by meng on 2007-01-25
> **logos34 said:**
> Do you mean 'partitions' when you say 'drives'?  Or do you have other hard disks in addition to the 250gb sata that's showing up?
Based on the output of his 'fdisk -l' command, it looks like he means different partitions on the same drive (2 ntfs + 1 fat = 3). However, Windows users become accustomed to talking about drives when they really mean partitions.

---

### Post by kostaschatzi on 2007-01-25
I have done it like the following now.

GNU nano 1.3.12             File: /etc/fstab:                       Modified  

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=8eb0195a-d164-4eac-838c-b89a5ddbebb9 / ext3 defaults,erro$
# /dev/sda7
UUID=29227b60-28c4-4979-ae3a-295868576edd none swap sw $
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
#/dev/sda5 /media/fat-sda5 vfat iocharset=utf8,umask=000 0 0
#/dev/sda1 /media/ntfs-sda1 ntfs nls=utf8,umask=0222 0 0
#/dev/sda6 /media/ntfs-sda6 ntfs nls=utf8,umask=0222 0 0





Do I use the last command and topic over?

---

### Post by meng on 2007-01-25
You should remove the # from the last three lines. # means the line will be ignored.

---

### Post by kostaschatzi on 2007-01-25
I indeed meant partitions :-))

I am not accustomed to anything.It s just that i thought that it would not make a difference

I will try to be a bit more careful in the way i express myself

---

### Post by kostaschatzi on 2007-01-25
I did this.Will i somehow save this configuration?

---

### Post by meng on 2007-01-25
Yes. ctrl-x to exit nano (the text editor)

Then

sudo mount -a

should mount everything for you.

---

### Post by kostaschatzi on 2007-01-25
It is asking me to give a name to this configuration.Is there a specific name i have to give it?

---

### Post by kostaschatzi on 2007-01-25
File Name to Write: /etc/fstab:                                                 
^G Get Help         ^T To Files         M-M Mac Format      M-P Prepend
^C Cancel           M-D DOS Format      M-A Append          M-B Backup File

What do i do to this?

---

### Post by kostaschatzi on 2007-01-25
Thank you very much guys.

It seems that everything was mounted.

But a few posts ago you told me that there will be an icon on my desktop of each mounted partition.Why is there not?

---

### Post by kostaschatzi on 2007-01-26
Guys i really wanted to thank you.

Of course i have met a lot of problems in other sections but however i have managed apart from mounting,also to make the partitions appear on my desktop

Thanks again
kostas

---

