---
title: "Mount ntfs volume of broken disk"
date: 2013-05-22
forum: Hardware
---

### Post by verbin on 2013-05-22
Hey all,

I'm trying to mount a half broken disk to backup some data for a costumer, so it's the first time I'm using a Linux OS to do this.

When i do a 
```
sudo fdisk -l
```
I get the following output
```
administrator@HC-RECBAC:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008487c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968454143   484226048   83  Linux
/dev/sda2       968456190   976771071     4157441    5  Extended
/dev/sda5       968456192   976771071     4157440   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16bbd131

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    25173854    12586896   27  Hidden NTFS WinRE
/dev/sdb2   *    25173855    25382699      104422+   7  HPFS/NTFS/exFAT
/dev/sdb3        25382700   488395119   231506210    7  HPFS/NTFS/exFAT

```

Its all about the sdb3 partition, so i tried to mount it with 
```
sudo mount -t ntfs /dev/sdb3 /mnt/disk
```

I get the following error:
```
administrator@HC-RECBAC:~$ sudo mount -t ntfs /dev/sdb3 /mnt/disk
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=10 count=1 br=-1: Input/output error
Failed to open inode FILE_UpCase: Input/output error
Failed to mount '/dev/sdb3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

Is there any other option to get some data from the disk?

---

### Post by Mark Phelps on 2013-05-22
Yes ... use a Windows app to recover the data from the Windows filesystem ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by verbin on 2013-05-23
Thank you for your reply i will try this.

---

