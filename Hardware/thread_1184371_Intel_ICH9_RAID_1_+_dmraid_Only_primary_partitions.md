---
title: "Intel ICH9 RAID 1 + dmraid: Only primary partitions available"
date: 2009-06-11
forum: Hardware
---

### Post by VooDooTom on 2009-06-11
Hi there,

after destoying myself some data by not installing dmraid on Ubuntu 9.04 and the Intel ICH9 chip, I finally managed it to get the system to work with my RAID 1 set. I have two 300GB HDDs (/dev/sdb and /dev/sdc) which are in the RAID 1 set I want to use in Ubuntu.
After installing dmraid I get some new devices and the old partitions on sdb and sdc are not available anymore in /dev (like sdc1 etc., what makes sense). The new devices are placed in /dev/mapper/ and have the following names:
```

control
isw_dbbdjdbeie_Volume_0
isw_dbbdjdbeie_Volume_01
isw_dbbdjdbeie_Volume_02
isw_dbbdjdbeie_Volume_03

```

I can mount the three devices ..01, ..02 and ..03 and use them for read/write access. All the partitions on the hard disk are NTFS formated.
Well, the problem is that there are not only three partitions, but, "inside" an extended partition, there are three more.

fdisk -l /dev/mapper/isw_dbbdjdbeie_Volume_0 gets me:
```

Disk /dev/mapper/isw_dbbdjdbeie_Volume_0: 300.0 GB, 300066872832 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x899097b3

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dbbdjdbeie_Volume_0p1   *           1       18249   146577404    7  HPFS/NTFS
/dev/mapper/isw_dbbdjdbeie_Volume_0p2           18249       22073    30720000    7  HPFS/NTFS
/dev/mapper/isw_dbbdjdbeie_Volume_0p3           22073       24623    20480000    7  HPFS/NTFS
/dev/mapper/isw_dbbdjdbeie_Volume_0p4           24623       36482    95256576    f  W95 Ext'd (LBA)
/dev/mapper/isw_dbbdjdbeie_Volume_0p5           24623       28447    30720000    7  HPFS/NTFS
/dev/mapper/isw_dbbdjdbeie_Volume_0p6           28447       30360    15360000    7  HPFS/NTFS
/dev/mapper/isw_dbbdjdbeie_Volume_0p7           30360       36482    49173504    7  HPFS/NTFS

```

Strange is that the device names not available. At least not with the "pX" at the end.

The output of "dmraid -ay" is:
```

RAID set "isw_dbbdjdbeie_Volume_0" already active
ERROR: dos: partition address past end of RAID device
RAID set "isw_dbbdjdbeie_Volume_01" already active
RAID set "isw_dbbdjdbeie_Volume_02" already active
RAID set "isw_dbbdjdbeie_Volume_03" already active

```

Line two seems so be a problem, but I read only about it for RAID 0, 5 or 10 (if I remember correctly) - unfortunately with no solution.
On booting up there occurs four times the line "no block devices found", in case this has something to do with it.

The question is: How do I get the remaining, not visible partitions to mount?

**Edit:** The "ERROR: dos: partition address past end of RAID device" error occurs still and I found an entry on launchpad that a bug causing this was fixed in the last dmraid version. I have the 1.0.0.rc15 version of dmraid from 2008-09-17, and will try to get the newer dmraid and hopefully it will work.

Thank you in advance,
Tom

---

### Post by VooDooTom on 2009-06-14
Bump :)

I tryed the current launchpad PPA version of dmraid from [https://launchpad.net/~themuso]("https://launchpad.net/~themuso"), but this did not fix the problem. I have still the same issues :(

Does anyone know a direction to point me in?
Thanks in advance,
Tom

---

### Post by Lepy on 2009-06-14
I'm also looking for a solution to a very similar problem. I have a Asus P5K Deluxe with an ICH9R that is running a 1TB RAID 1 perfectly in WinXP and Win7 for data backup formatted in NTFS. 

However, in 9.04 32bit, sudo dmraid -ay gives:
```
RAID set "isw_dfjeaigaha_Media" already active
ERROR: dos: partition address past end of RAID device
```

sudo fdisk -l /dev/mapper/isw_dfjeaigaha_Media returns:
```
Disk /dev/mapper/isw_dfjeaigaha_Media: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eb16b

                           Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dfjeaigaha_Media1               1      121601   976760001    7  HPFS/NTFS
```

First, to fstab I tried adding 
```
/dev/mapper/isw_dfjeaigaha_Media /media/F ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

However, it gave a resource not found on boot for the /dev/mapper/isw_dfjeaigaha_Media. Since fdisk lists it as /dev/mapper/isw_dfjeaigaha_Media1, I have considered adding a 1 to the end in fstab, but at this point I'm more concerned with retaining the data on the drives instead of experimenting.

Sorry to be of no help, but at least you aren't alone.

---

### Post by ronparent on 2009-06-15
VooDooTom - you might try looking at what is shown in the partitioner (gparted). In a raid1 set the partioning would normally show identical for the raid set, sda and sdb. You won't be able to mount anything not showing in /dev/mapper.

Lepy - /dev/mapper/isw_dfjeaigaha_Media represents the drive and has no file system. What is mountable is /dev/mapper/isw_dfjeaigaha_Media1 or any partitions shown in /dev/mapper ending with a number.

---

### Post by VooDooTom on 2009-06-16
ronparent, thank you for your suggestion. The partitioner gparted sees the whole raid 1 set (/dev/mapper/isw_dbbdjdbeie_Volume_0) as unallocated memory. The message "Can't have a partition outside the disk!" appears at the start of the program.
sdb and sdc look identical and the first three mounted partitions of the raid set are fitting to the primaray partitions on sdb and sdc.
So why can gparted not see the partitions on /dev/mapper/isw_dbbdjdbeie_Volume_0, but fdisk can?

@Lepy: What version of dmraid are you using?

Meanwhile I tryed with the latest git version and with previous 1.0.0.rc14 - both brought up the same error. Is there maybe anything besides dmraid, that could make such an error occur?

Thanks for your help,
Tom

---

### Post by Lepy on 2009-06-16
VooDooTom - I've only installed the version in the jaunty repositories, 1.0.0.rc15-6ubuntu2 and not having much luck with it, but I've been concentrating on getting my mythtv box working, which is turning out to be a task in itself.

ronparent - To fstab, I tried adding both (separately)

```
/dev/mapper/isw_dfjeaigaha_Media1 /media/F ntfs defaults,locale=en_US.UTF-8 0 0
and
/dev/mapper/isw_dfjeaigaha_Media1 /media/F ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

and both configs returned a failed mount on boot and neither sdb or sdc (the RAID 1 drives) are shown in the nautilus places bar. GParted shows /dev/mapper/isw_dfjeaigaha_Media as unallocated space while sdb and sdc are shown properly as ntfs, but neither reports used or unused space.

---

### Post by VooDooTom on 2009-06-16
Lepy, maybe you could try what happens with other versions. Recently, there was a bugfix for an error resulting in the same message ("ERROR: dos: partition address past end of RAID device"). The report and comments on it can be found on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/337284"). But since you have also the 1.0.0.rc15-6ubuntu2 version installed, it seems that there is another issue, which might be the same as mine.

For testing your configuration you do not need to restart, you could also try to mount on the command line:
```

sudo mount -t ntfs-3g /dev/mapper/isw_dfjeaigaha_Media1 /media/F
```
As "dmraid -ay" did not activate any partitions, you currently cannot mount anything. A look into the /dev/mapper folder will tell you the same, since there is no file isw_dfjeaigaha_Media file with a (partition) number at the end. So unless "dmraid -ay"  does not come up with something like the ouput on my system, you will not be able to mount anything (I just have the problem that not all partitions get mounted).

Regards,
Tom

---

### Post by ronparent on 2009-06-16
VooDooTom - dmraid doesn't in fact write anything to the drives, only discovers what's there in the metedata section of the drives. Anything that may have been done to alter those drives may have been done before dmraid was installed. Since the drives are ntfs, if you can still access them thru windows you best bet may be to do that and run filesystem checks in windows. That should clear up any fs conflicts that may be present on the drives. If you cannot access them in windows, then we may have a big problem restoring them without data loss, Incidently your assessment of Lepy's situation was incisive.

---

### Post by VooDooTom on 2009-06-18
Thank you for the hint, unfortunately nothing has changed with dmraid, though some corrections had windows' chkdsk done :(.

---

