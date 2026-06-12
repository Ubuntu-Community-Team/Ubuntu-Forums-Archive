---
title: "external harddrive (NTFS) not functioning"
date: 2010-06-21
forum: Hardware
---

### Post by eatingaltoids on 2010-06-21
Hi,

I bought an external harddrive some time ago but it is acting strange since a week or so.

It's a Samsung S2 Portable (500GB) and it is 1 big NTFS partition.

it worked flawlessly until last week: it was unable to mount on my ubuntu system and windows said it needed to be formatted. After a chkdsk /f it worked under windows again but not under ubuntu.

I formatted the drive but the problem still persists.

this is what I get when I plug it in:

```
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=6 count=1 br=-1: Input/output error
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

can't find anything usefull on google or here.

booting with "mike@mike-desktop:~$ sudo ntfs-3g /dev/sdb1 /home/mike/mount" doesn't mount it either.

The thing is, EVERYTHING is working now on windows, just not on ubuntu

(I need the drive to be NTFS)

---

### Post by dino99 on 2010-06-21
check your bios, and choose ahci mode

ubuntu (linux in general) directly deal with ntfs using ntfsprogs, and windows is able to work with linux formats like ext2, ext3, ext4, so there is no problem to use something else than ntfs.[http://www.fs-driver.org/](http://www.fs-driver.org/)

you need to remove raid config if any: sudo dmraid -rE

then check this hdd with partedmagic to make a good formatting

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by eatingaltoids on 2010-06-22
my bios doesn't have an ahci mode (atleast, can't find it)

fixed it with parted magic, where partition magic and gparted fail.

The problem with this harddrive is that it has got a logical sector size of 1024, while this isn't much supported yet. (Gparted showed the drive to be 238 MiB but couldn't fix it).

on the website of gparted it's stated that larger sector sizes are supported now but after downloading the latest tar.bz2 version and using ./configure it says:

> ================ Final configuration ===================
                 Installing into prefix  :  /usr/local

                   Build documentation?  :  yes

   Need part table re-read work around?  :  yes
    ** Supports sector sizes > 512 bytes?  :  no**

 If all settings are OK, type make and make install 
========================================================


in the end:
parted magic fixed it without a problem.


EDIT: how can I change the topic prefix to solved?

---

