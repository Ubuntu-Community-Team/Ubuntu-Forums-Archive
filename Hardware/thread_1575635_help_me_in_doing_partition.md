---
title: "help me in doing partition"
date: 2010-09-16
forum: Hardware
---

### Post by BAB SWAIN on 2010-09-16
hi
i want to make partition in my external hard drive (transcend 320 GB)i used kde partition manager.
but i did not success.
i found following msg
**KDE Partition Manager: Operation Report**

    Date: 2010-09-16 11:38   Program version: 1.0.1   LibParted version: 2.2   KDE version: 4.4.1 (KDE 4.4.1)   Machine: Linux babswain-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686   User ID: 0   
  **Create a new partition (149.05 GiB, ntfs) on ‘/dev/sdb’**    **Job: Create new partition on device ‘/dev/sdb’**  
**Create new partition ‘/dev/sdb1’: Success**
 
    **Job: Create file system ntfs on partition ‘/dev/sdb1’**    **Command: mkfs.ntfs -f -vv /dev/sdb1**  Cluster size has been automatically set to 4096 bytes. Creating NTFS volume structures. Creating root directory (mft record 5) Creating $MFT (mft record 0) Creating $MFTMirr (mft record 1) Creating $LogFile (mft record 2) Creating $AttrDef (mft record 4) Creating $Bitmap (mft record 6) Creating $Boot (mft record 7) Creating backup boot sector. Creating $Volume (mft record 3) Creating $BadClus (mft record 8) Creating $Secure (mft record 9) Creating $UpCase (mft record 0xa) Creating $Extend (mft record 11) Creating system file (mft record 0xc) Creating system file (mft record 0xd) Creating system file (mft record 0xe) Creating system file (mft record 0xf) Creating $Quota (mft record 24) Creating $ObjId (mft record 25) Creating $Reparse (mft record 26) Syncing root directory index record. Syncing $Bitmap. Syncing $MFT. Updating $MFTMirr. Syncing device. Syncing device. FAILED  

  **Create file system ntfs on partition ‘/dev/sdb1’: Success**
 
    **Job: Set the file system label on partition ‘/dev/sdb1’ to "BAB SWAIN1"**    **Command: ntfslabel --force /dev/sdb1 BAB SWAIN1**  

  **Set the file system label on partition ‘/dev/sdb1’ to "BAB SWAIN1": Error**
 
  [B]Create a new partition (149.05 GiB, ntfs) on ‘/dev/sdb’: Error

pl help me on this matter.
thnks and regards
bab swain
[/B]

---

### Post by sanderd17 on 2010-09-16
I (and most ubuntu users) use Gparted for their partitions. You can install Gparted via the normal way to install apps or via command line:

```

sudo apt-get install gparted

```

Maybe try this and report if it doesn't work with gparted.

---

### Post by BAB SWAIN on 2010-09-16
Thnks alot for your replay. i have also with gparted and found following message. i am suspecting that, external hard drive may have bad sector. also disc utility showing status of  DISK FAILURE IS IMMINENT. how can i corrected bad sector by using any good linux software.
thank you.







GParted 0.5.1
 Libparted 2.2
    **Create Primary Partition #1 (ntfs, 149.05 GiB) on /dev/sdb**  00:09:33    ( ERROR )             calibrate New Partition #1  00:00:04    ( SUCCESS )             [I]path: /dev/sdb-1
start: 63
end: 312576704
size: 312576642 (149.05 GiB)[/I]          create empty partition  00:00:50    ( SUCCESS )             [I]path: /dev/sdb1
start: 63
end: 312576704
size: 312576642 (149.05 GiB)[/I]          set partition type on /dev/sdb1  00:00:31    ( SUCCESS )             *new partition type: ntfs*          create new ntfs file system  00:08:08    ( ERROR )             ***mkntfs -Q -v -L "" /dev/sdb1***             [I]Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
[/I]       *Syncing device. FAILED*

---

