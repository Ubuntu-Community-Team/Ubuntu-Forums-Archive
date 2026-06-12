---
title: "Intel RAID 5 with mdadm makes me crazy"
date: 2011-08-08
forum: Hardware
---

### Post by iwan.z on 2011-08-08
Hello Everyone,
I am not that new to Ubuntu and I was able to find for almost every problem I got a solution, but not this one. I googled for some weeks and asked everyone I know about the problem but without any luck. The last possibility to find a solution is this forum.

I bought some new components to upgrade my old PC. So I bought:

[LIST]
[*]Intel Core i7-2600k
[*]Asrock Z68 Extreme4 (with 82801 SATA RAID Controller on it)
[*]Some RAM and so on
[/LIST]
I also wanted to reuse my four old  SAMSUNG HD103UJ 1 TB hard drives. In the past I used mdadm as fake raid level 5 and everything worked just fine. Now with the upgrade I wanted to use the RAID Controller on my mainboard.

So what I did was:

[LIST=1]
[*]Activated RAID functionality in BIOS and created an array with the ROM Tool from Intel that told me I could use 2.7TB. :D
[*]Checked with my Windows 7 installation (used for some non-linux applications like TomTom) if I can access the Raid Array and work with it. 
Until here everything is perfect. I even created a ntfs partition for testing purposes.
[*]Used a fresh installation of natty + gnome 3
-- Here the odyssey starts --
[*]I googled if a how to is available to use mdadm with the raid array and found this page [http://bertrandbenoit.blogspot.com/2011/07/manage-intel-raid-under-gnulinux-using.html](http://bertrandbenoit.blogspot.com/2011/07/manage-intel-raid-under-gnulinux-using.html)
The page is really great (thanks for it)
Information about my Raid:
```

# mdadm --detail-platform
       Platform : Intel(R) Matrix Storage Manager
        Version : 10.6.0.1091
    RAID Levels : raid0 raid1 raid10 raid5
    Chunk Sizes : 4k 8k 16k 32k 64k 128k
      Max Disks : 7
    Max Volumes : 2
 I/O Controller : /sys/devices/pci0000:00/0000:00:1f.2
          Port0 : /dev/sda (ML0221F303XN3D)
          Port2 : /dev/sdb (S13PJ9AQ923317)
          Port3 : /dev/sdc (S13PJ9AQ923315)
          Port4 : /dev/sdd (S13PJ9AQ923313)
          Port5 : /dev/sdg (S13PJ9AQ923320)
          Port1 : - no device attached -

```I want to use the hard drives on ports 2-5.
[*]Scan with dmadm for already used raid arrays
```

# mdadm --assemble --scan
mdadm: Container /dev/md/imsm0 has been assembled with 4 drives

```After the command I can see in gnome-disk-utility -> [palimpsest]("http://en.wikipedia.org/wiki/Palimpsest_Disk_Utility") an inactive raid array /dev/md127 (seems to be the default imsm device name).  [URL="http://en.wikipedia.org/wiki/Palimpsest_Disk_Utility"]
[/URL]
[*]More information on the array is:
```

# mdadm -E /dev/md127
/dev/md127:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.3.00
    Orig Family : c96fa831
         Family : c96fa831
     Generation : 00000290
           UUID : 59e6dacc:af2b5b6d:924bc94b:9e18cf7a
       Checksum : 5e36dabe correct
    MPB Sectors : 2
          Disks : 4
   RAID Devices : 1

  Disk00 Serial : S13PJ9AQ923317
          State : active
             Id : 00020000
    Usable Size : 1953520654 (931.51 GiB 1000.20 GB)

[DATA]:
           UUID : 12ae87fa:5edef66f:7b4da071:676c648f
     RAID Level : 5
        Members : 4
          Slots : [UUUU]
      This Slot : 0
     Array Size : 5860560896 (2794.53 GiB 3000.61 GB)
   Per Dev Size : 1953520648 (931.51 GiB 1000.20 GB)
  Sector Offset : 0
    Num Stripes : 15261878
     Chunk Size : 64 KiB
       Reserved : 0
  Migrate State : idle
      Map State : normal
    Dirty State : clean

  Disk01 Serial : S13PJ9AQ923315
          State : active
             Id : 00030000
    Usable Size : 1953520654 (931.51 GiB 1000.20 GB)

  Disk02 Serial : S13PJ9AQ923313
          State : active
             Id : 00040000
    Usable Size : 1953520654 (931.51 GiB 1000.20 GB)

  Disk03 Serial : S13PJ9AQ923320
          State : active
             Id : 00050000
    Usable Size : 1953520654 (931.51 GiB 1000.20 GB)


```
[*]General details are:
```

# mdadm -E /dev/md127
/dev/md127:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.3.00
    Orig Family : c96fa831
         Family : c96fa831
     Generation : 00000290
           UUID : 59e6dacc:af2b5b6d:924bc94b:9e18cf7a
       Checksum : 5e36dabe correct
    MPB Sectors : 2
          Disks : 4
   RAID Devices : 1

  Disk00 Serial : S13PJ9AQ923317
          State : active
             Id : 00020000
    Usable Size : 1953520654 (931.51 GiB 1000.20 GB)

[DATA]:
           UUID : 12ae87fa:5edef66f:7b4da071:676c648f
     RAID Level : 5
        Members : 4
          Slots : [UUUU]
      This Slot : 0
     Array Size : 5860560896 (2794.53 GiB 3000.61 GB)
   Per Dev Size : 1953520648 (931.51 GiB 1000.20 GB)
  Sector Offset : 0
    Num Stripes : 15261878
     Chunk Size : 64 KiB
       Reserved : 0
  Migrate State : idle
      Map State : normal
    Dirty State : clean

  Disk01 Serial : S13PJ9AQ923315
          State : active
             Id : 00030000
    Usable Size : 1953520654 (931.51 GiB 1000.20 GB)

  Disk02 Serial : S13PJ9AQ923313
          State : active
             Id : 00040000
    Usable Size : 1953520654 (931.51 GiB 1000.20 GB)

  Disk03 Serial : S13PJ9AQ923320
          State : active
             Id : 00050000
    Usable Size : 1953520654 (931.51 GiB 1000.20 GB)

``````

# mdadm -D /dev/md127
/dev/md127:
        Version : imsm
     Raid Level : container
  Total Devices : 4

Working Devices : 4


           UUID : 59e6dacc:af2b5b6d:924bc94b:9e18cf7a
  Member Arrays :

    Number   Major   Minor   RaidDevice

       0       8       48        -        /dev/sdd
       1       8       32        -        /dev/sdc
       2       8       16        -        /dev/sdb
       3       8       96        -        /dev/sdg


``````

# mdadm -D /dev/md126
/dev/md126:
      Container : /dev/md/imsm0, member 0
     Raid Level : raid5
     Array Size : 2930280448 (2794.53 GiB 3000.61 GB)
  Used Dev Size : 976760320 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4

          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-asymmetric
     Chunk Size : 64K


           UUID : 12ae87fa:5edef66f:7b4da071:676c648f
    Number   Major   Minor   RaidDevice State
       3       8       16        0      active sync   /dev/sdb
       2       8       32        1      active sync   /dev/sdc
       1       8       48        2      active sync   /dev/sdd
       0       8       96        3      active sync   /dev/sdg

```
[*]mdstat has the following output:
```

# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdg[3](S) sdb[2](S) sdc[1](S) sdd[0](S)
      9028 blocks super external:imsm
       
unused devices: <none>

```
[*]I started the raid by entering the command:
```

# mdadm -I -e imsm /dev/md127
mdadm: Started /dev/md/DATA with 4 devices

```
[*]Now mdstat has the following output:
```

# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : active (read-only) raid5 sdb[3] sdc[2] sdd[1] sdg[0]
      2930280448 blocks super external:/md127/0 level 5, 64k chunk, algorithm 0 [4/4] [UUUU]
      
md127 : inactive sdg[3](S) sdb[2](S) sdc[1](S) sdd[0](S)
      9028 blocks super external:imsm
       
unused devices: <none>

```I learned that md126 is so long read only until it was used the first time.
[*]I wrote that I created one ntfs partition for testing. I could also see it + another systempartition created by windows. I was able to remove the partition using windows, but I could not remove the systempartition. So now I have the device /dev/md126p1.
To be able to do any changes I set the readwrite flag to the partition
```

# mdadm --readwrite /dev/md126p1 

```
[*]The state of the Raid md126 container changed to **clean**.
[*]Now if I want to do any changes to the partition or create a new one I see the state **write-pending**. This state never changes.
[/LIST]
I do not know what to do from now on. When using the command below I see that the superblock is not persistent:
```

# mdadm --detail /dev/md126p1
/dev/md126p1:
        Version : 0.90
     Raid Level : raid5
     Array Size : 131072 (128.02 MiB 134.22 MB)
  Used Dev Size : 976760320 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 126
    Persistence : Superblock is not persistent

          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-asymmetric
     Chunk Size : 64K

    Number   Major   Minor   RaidDevice State
       3       8       16        0      active sync   /dev/sdb
       2       8       32        1      active sync   /dev/sdc
       1       8       48        2      active sync   /dev/sdd
       0       8       96        3      active sync   /dev/sdg

```But I do not know what to do about it. 
The raid array is also gone after I reboot the system. I already stored the configuration file mdadm.conf in /etc and /etc/mdadm/. The content is the following:
```

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY metadata=imsm UUID=59e6dacc:af2b5b6d:924bc94b:9e18cf7a
ARRAY /dev/md/DATA container=59e6dacc:af2b5b6d:924bc94b:9e18cf7a member=0 UUID=12ae87fa:5edef66f:7b4da071:676c648f

# This file was auto-generated on Mon, 01 Aug 2011 22:35:13 +0200
# by mkconf $Id$

```Can anyone help me? What am I doing wrong??? What is missing? It really makes me crazy ](*,)

Every help is appreciated.

Thanks,

Iwan

---

### Post by iwan.z on 2011-08-25
Hi Everyone,
I found the root cause of the problem with some help from the linux-raid distribution list. I was using mdadm 3.1.4, it is in the repository of  ubuntu 11.04. This version does not really support IMSM that this is the real  problem. I found it because I did not have mdmon. It does not exists in  this old version. So I downloaded the latest official relesae 3.2.1 and  installed it via make && sudo make install. I could not find any deb-packages for this version. Now everything works  perfectly. The array is available after reboot and the synchronization  process works over BIOS and not over mdadm itself. 

Finally I can use my raid! \\:D/

Cheers,

Iwan

p.s. Dear moderators, could you please mark this thread as solved? Thanks.

---

### Post by sitg on 2011-08-30
> **iwan.z said:**
> Hi Everyone,
I found the root cause of the problem with some help from the linux-raid distribution list. I was using mdadm 3.1.4, it is in the repository of  ubuntu 11.04. This version does not really support IMSM that this is the real  problem. I found it because I did not have mdmon. It does not exists in  this old version. So I downloaded the latest official relesae 3.2.1 and  installed it via make && sudo make install. I could not find any deb-packages for this version. Now everything works  perfectly. The array is available after reboot and the synchronization  process works over BIOS and not over mdadm itself. 

Finally I can use my raid! \\:D/

Cheers,

Iwan

p.s. Dear moderators, could you please mark this thread as solved? Thanks.

:KS
it works,thank you.

---

### Post by yantsa on 2011-09-07
After 3days, this post seems to be the sollution to my "headache". 

Could you please explain how to use mdadm 3.2 instead of 3.1.4? I am trying to do the same, but with now luck. During installation?

Please advise

---

### Post by anupcshan on 2012-01-12
> **iwan.z said:**
> Hi Everyone,
I found the root cause of the problem with some help from the linux-raid distribution list. I was using mdadm 3.1.4, it is in the repository of  ubuntu 11.04. This version does not really support IMSM that this is the real  problem. I found it because I did not have mdmon. It does not exists in  this old version. So I downloaded the latest official relesae 3.2.1 and  installed it via make && sudo make install. I could not find any deb-packages for this version. Now everything works  perfectly. The array is available after reboot and the synchronization  process works over BIOS and not over mdadm itself. 

Finally I can use my raid! \\:D/

Cheers,

Iwan

p.s. Dear moderators, could you please mark this thread as solved? Thanks.

Thanks a *lot* for the hint.

---

