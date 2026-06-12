---
title: "Mount Existing Damaged RAID1 array"
date: 2017-10-31
forum: Hardware
---

### Post by owne on 2017-10-31
Hi There - I had a 3TB disk fail in a synology DS unit previously and i am looking to recover whatever data i can on it. The data recovered would be nice to have, but it is not super critical. The disk used to be one of two in a JBOD arrangement - but i believe it was formatted as a Synology Hybrid RAID (so a single disk in a RAID1 "array").

The state of play is that I have

[LIST=1]
[*]used ddrescue to copy the contents of the 3TB drive to an unused 6TB drive. Approximately 1GB could not be recovered according to the output
[*]after restarting, the 6TB copy appears to have mounted a RAID array (md127) under sda5
[*]when trying to mount, the superblock error occurs
[/LIST]

Outputs:

```
owen@owen-P65-P67RGRERA:~$ lsblk -o name,label,size,fstype,model
NAME      LABEL                    SIZE FSTYPE            MODEL
sdd                              465.8G                   Samsung SSD 850 
&#9492;&#9472;sdd2                           465.7G ext4              
sdb                                2.7T                   ASM1156-PM      
&#9500;&#9472;sdb2                               2G                   
&#9500;&#9472;sdb5                             2.7T                   
&#9492;&#9472;sdb1                             2.4G                   
sdc                              465.8G                   Samsung SSD 850 
&#9500;&#9472;sdc2                           433.3G ext4              
&#9500;&#9472;sdc3                              32G swap              
&#9492;&#9472;sdc1                             512M vfat              
sda                                5.5T                   ASM1156-PM      
&#9500;&#9472;sda2                               2G swap              
&#9500;&#9472;sda5    owen-P65-P67RGRERA:100   2.7T linux_raid_member 
&#9474; &#9492;&#9472;md127                          2.7T                   
&#9492;&#9472;sda1                             2.4G linux_raid_member
```

sdb is the original, sda is the copy. sdc and sdd are unrelated.

[SIZE=2]```
owen@owen-P65-P67RGRERA:~$ cat /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md127 : active (auto-read-only) raid1 sda5[0]
      2925401792 blocks super 1.2 [1/1] [U]
      bitmap: 0/22 pages [0KB], 65536KB chunk

unused devices: <none>
```[/SIZE]

```
owen@owen-P65-P67RGRERA:~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 5.5 TiB, 6001175126016 bytes, 11721045168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: 6BB75B84-5068-4315-9D30-FCAC987C89B9

Device       Start        End    Sectors  Size Type
/dev/sda1      256    4980735    4980480  2.4G Linux RAID
/dev/sda2  4980736    9175039    4194304    2G Linux RAID
/dev/sda5  9453280 5860519007 5851065728  2.7T Linux RAID
```

```
owen@owen-P65-P67RGRERA:~$ sudo mdadm --examine /dev/sda5
/dev/sda5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : f4c560cf:7b6e213a:cf358cf0:016bd8fe
           Name : owen-P65-P67RGRERA:100  (local to host owen-P65-P67RGRERA)
  Creation Time : Fri Oct 27 11:46:34 2017
     Raid Level : raid1
   Raid Devices : 1

 Avail Dev Size : 5850803584 (2789.88 GiB 2995.61 GB)
     Array Size : 2925401792 (2789.88 GiB 2995.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : active
    Device UUID : d339a94d:0b9dcbc6:acbb4da9:d7bc8492

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri Oct 27 11:46:34 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : b120a3f4 - correct
         Events : 0


   Device Role : Active device 0
   Array State : A ('A' == active, '.' == missing, 'R' == replacing)
```

```
owen@owen-P65-P67RGRERA:~$ sudo mdadm -D /dev/md127 
/dev/md127:
        Version : 1.2
  Creation Time : Fri Oct 27 11:46:34 2017
     Raid Level : raid1
     Array Size : 2925401792 (2789.88 GiB 2995.61 GB)
  Used Dev Size : 2925401792 (2789.88 GiB 2995.61 GB)
   Raid Devices : 1
  Total Devices : 1
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Fri Oct 27 11:46:34 2017
          State : clean 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : owen-P65-P67RGRERA:100  (local to host owen-P65-P67RGRERA)
           UUID : f4c560cf:7b6e213a:cf358cf0:016bd8fe
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5

```

When trying to mount:

```
owen@owen-P65-P67RGRERA:~$ sudo mount /dev/md127 /media/storage
mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

dmesg does not seem to have meaningful information on this - the only relevant part is that it says sdb has problems.

```
owen@owen-P65-P67RGRERA:~$ sudo dumpe2fs /dev/sda5
dumpe2fs 1.42.13 (17-May-2015)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda5
Couldn't find valid filesystem superblock.
```

So working under the assumption that the superblock doesn't work - i guess the focus is on how to repair it.

```
owen@owen-P65-P67RGRERA:~$ sudo mke2fs -n /dev/md127 
mke2fs 1.42.13 (17-May-2015)
Creating filesystem with 731350448 4k blocks and 182845440 inodes
Filesystem UUID: 5dd53324-560e-4527-b73d-a244bc0dec78
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848, 512000000, 550731776, 644972544
```

I had previously tried to restore the superblocks (using e2fsck) but i'm pretty sure i did it wrong so i had to re-rescue. Also sda was previously it's own formatted disk, and i used a quick method to clear existing partitions:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

Not sure if that's relevant.

---

### Post by jagdtigger on 2017-11-02
Hi!

Hm, is it possible that there is a raid0 sitting on top of the raid1? Since mdadm mounted the original raid array as read only it wont hurt to try and mount md127 as a one disk raid0 array.

---

### Post by owne on 2017-11-02
Thanks for the suggestion - I'm curious as to what leads you to the possibility of raid0? Was it just the mdadm mounting as read-only? Doesn't raid0 require at least 2 drives for usable data? My crude understanding of raid0 is that one drive does "even" sectors while the other does "odd". And that no single drive can adequately describe the disks data.

I figure raid1 is a default for Synology since one drive can describe all the necessary data for recovery. If a user wants to step up and add another disk for redundancy, i figure with the first one being arranged already for raid1, it makes the process much easier?

Anyway, since a reboot, a few other things have changed, one of which is the read-only state:

```
owen@owen-P65-P67RGRERA:~$ cat /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md100 : active raid1 sda5[0]
      2925401792 blocks super 1.2 [1/1] [U]
      bitmap: 0/22 pages [0KB], 65536KB chunk

unused devices: <none>
```

Several other things have changed since a reboot, namely fdisk now reports a backup GPT table is corrupt. This happened the first time i did a ddrescue but strangely not the second?

```
owen@owen-P65-P67RGRERA:~$ sudo fdisk -l /dev/sda
**The backup GPT table is corrupt, but the primary appears OK, so that will be used.**
Disk /dev/sda: 5.5 TiB, 6001175126016 bytes, 11721045168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: 6BB75B84-5068-4315-9D30-FCAC987C89B9

Device       Start        End    Sectors  Size Type
/dev/sda1      256    4980735    4980480  2.4G Linux RAID
/dev/sda2  4980736    9175039    4194304    2G Linux RAID
/dev/sda5  9453280 5860519007 5851065728  2.7T Linux RAID
```

mdadm cannot examine sda5:

```
owen@owen-P65-P67RGRERA:~$ sudo mdadm --examine /dev/sda5
mdadm: No md superblock detected on /dev/sda5.
```

... and details on the md device are now missing the name/UUID/events part. Otherwise looks the same

```
owen@owen-P65-P67RGRERA:~$ sudo mdadm -D /dev/md100
/dev/md100:
        Version : 1.2
  Creation Time : Fri Oct 27 11:46:34 2017
     Raid Level : raid1
     Array Size : 2925401792 (2789.88 GiB 2995.61 GB)
  Used Dev Size : 2925401792 (2789.88 GiB 2995.61 GB)
   Raid Devices : 1
  Total Devices : 1
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Fri Oct 27 11:46:34 2017
          State : clean 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
```

Also the output from fsck:

```
owen@owen-P65-P67RGRERA:~$ sudo fsck.ext4 -fn /dev/md100
e2fsck 1.42.13 (17-May-2015)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/md100
Could this be a zero-length partition?
```

From my thinking... all signs point to a superblock problem, but what i'm struggling to understand is whether the attempting to recover superblocks (e2fsck -b <superblock backup>) is done on the base parition device (sda5) or the RAID device (md100).

I think superblock recovery is supposed to be done on sda5 (not md100), which i understand would require mdadm to stop/remove md100, then try recovering a few superblocks and re-assembling (or creating?). I get confused, does mdadm create potentially destroy data?

Thanks in advance

---

### Post by jagdtigger on 2017-11-03
Sorry, i mixed up JBOD and raid0 again. JBOD VS RAID0:
> raid0 means the data is striped over 2 disks.
JBOD means your file is either on disk 1 or disk 2.
Also read [http://www.buzzle.com/articles/raid0-vs-jbod.html](http://www.buzzle.com/articles/raid0-vs-jbod.html) to get more details.

Whats important.
If one disk fails in raid0 you lost all your data since its striped over 2 disks.
If one disk fails in JBOD you just loose the files on that one disk and the data on the other disk is ok.

The  advantage of raid0 though is more read/write performance although i  wonder if single disk speeds are a bottleneck in a J version.
I think cpu would be more of a bottleneck so i am not sure if you would get a real performance gain with raid0.
[https://forum.synology.com/enu/viewtopic.php?t=56651](https://forum.synology.com/enu/viewtopic.php?t=56651)

According to a zyxel guide this command should reassemble the JBOD:
mdadm -A -f /dev/md0 /dev/md100

[ftp://ftp.zyxel.it/guide/nas/nsa_recovery_linux.pdf](ftp://ftp.zyxel.it/guide/nas/nsa_recovery_linux.pdf)

---

### Post by owne on 2017-11-07
For completeness I tried but had this response:

```
owen@owen-P65-P67RGRERA:~$ sudo mdadm -A -f /dev/md9 /dev/md100
mdadm: no recogniseable superblock on /dev/md100
mdadm: /dev/md100 has no superblock - assembly aborted
```

That said i was surprised it did anything. Generally when assembling you define a target md from one or more source physical devices (/dev/sd[X]).

Still the superblock question..

---

