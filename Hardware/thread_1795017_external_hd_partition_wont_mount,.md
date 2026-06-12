---
title: "external hd partition wont mount,"
date: 2011-07-01
forum: Hardware
---

### Post by philipballew on 2011-07-01
I try to mount my external hd and only 1 partition of 2 mounts. i get this error```
Unable to mount Elements

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

---

### Post by oldfred on 2011-07-01
Is this a NTFS partition? If so, have you run chkdsk recently on the NTFS partition?

You will proably get the same error, but post this:

```
sudo fdisk -lu
```

---

### Post by philipballew on 2011-07-02
its ntfs. but its just file storage. I don't run windows here. lets see what it says```
philip@philip-Studio-1558:~$ sudo fdisk -lu
[sudo] password for philip: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ab5db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    28313231    14155592   83  Linux
/dev/sda2        28313598   976773119   474229761    5  Extended
/dev/sda5       954208256   976773119    11282432   82  Linux swap / Solaris
/dev/sda6        28313600   946237439   458961920   83  Linux
/dev/sda7       946239488   954195967     3978240   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dedf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  2297049087  1148523520    7  HPFS/NTFS
/dev/sdb2      2297049088  3907024895   804987904   83  Linux
philip@philip-Studio-1558:~$ 

```

---

### Post by oldfred on 2011-07-02
It still may need chkdsk. chkdsk has nothing to do with whether you have an operating system or not, but whether the NTFS file system is starting to  have issues.

---

### Post by philipballew on 2011-07-02
Im pretty sure i was copying files to it, and i unpluged the external drive right before it stopped working

---

### Post by philipballew on 2011-07-02
Im pretty sure i was copying files to it, and i unpluged the external drive right before it stopped working

---

### Post by oldfred on 2011-07-02
Abnormal shutdown is one of the main causes of needing chkdsk on NTFS or e2fsck on ext family of formats. If an external drive you need to cleanly unmount before removing.

Also dual booting with windows and hibernating in windows can cause problems. The hibernation is looking for a file in a certain place which if you copy something from Ubuntu it may have moved a file. Then the hibernation is corrupted the file system.

---

### Post by philipballew on 2011-07-02
What would you recommend as a way to pull off all date before i restore and format? and should I format to a ext file system say?

---

### Post by oldfred on 2011-07-02
If you are not running windows nor need window to ever read the drive, then I would format to ext4 or ext3. Also you can only run chkdsk from Windows, so you have to have at least a windows repairCD. You will have to have backups as changing format will erase everything. 

Do you want all your data in one very large partition or perhaps several smaller one's. With smaller one's it does become more of an issue to manage sizes but if one partition has corruption then the whole drive is not corrupted.

If chkdsk does not repair it then you can try testdisk or photorec to recover data.

This will not do a full chkdsk:
In windows run "chkdsk /f". Although you can also use "ntfsfix" in Ubuntu:
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXY x- drive y - partition

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk". If not a boot partition it will set flag and Ubuntu will not mount it with flag set.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

