---
title: "Help re-assembling Raid-5 array with mdadm"
date: 2008-09-18
forum: General Help
---

### Post by zhenya on 2008-09-18
I have a 4 disk raid-5 array that I was attempting to add two new disks to.  I had some trouble adding the disks, and now I can no longer start the existing raid array.  I think that I accidentally added a couple of drives with the wrong name, such that mdadm thinks that I now have an 8 disk array using two spares.  At this point, I'd just like to be able to start the original 4 disk array again.

When I run the command: 
```
 mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

I am returned the result: 
```
mdadm: superblock on /dev/sdc1 doesn't match others - assembly aborted
```

Here is the result of examining one of the disks in the array:
```
zhenya@fileserver:/mnt/Storage$ sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.91.01
           UUID : b4e69c35:76ced9c8:72f4efcf:c87e2502
  Creation Time : Thu Mar 15 00:28:28 2007
     Raid Level : raid5
    Device Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 1953543680 (1863.04 GiB 2000.43 GB)
   Raid Devices : 6
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 28654400 (27.33 GiB 29.34 GB)
  Delta Devices : 2 (4->6)

    Update Time : Wed Sep 17 04:58:48 2008
          State : clean
 Active Devices : 6
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 2
       Checksum : b9dcc9c5 - correct
         Events : 0.299874

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       65        2      active sync   /dev/.static/dev/sde1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/.static/dev/sde1
   3     3       8       81        3      active sync   /dev/.static/dev/sdf1
   4     4       8       16        4      active sync   /dev/sdb
   5     5       8        0        5      active sync   /dev/sda
   6     6       8       17        6      spare   /dev/sdb1
   7     7       8        1        7      spare   /dev/sda1

```

This shows the 8 devices (I only have 6, and would be happy just getting the original 4 mounted again).  How do I remove the non-existent drives (sda and sdb), and how can I re-assemble my original array?  Please help!  

Thank you!

---

### Post by fjgaude on 2008-09-18
Without knowing exactly what you did to add drives to an existing array it's hard to say what we have here.

One thing you might try is to uninstall mdadm, delete the /etc/mdadm/mdadm.conf file, reboot. Then after the OS is up from the repository install mdadm. The run this:

```
sudo mdadm --assemble --scan
```

Don't name the drives as mdadm will scan for the UUID and assemble from the ones that match the array UUID.

Good luck!

---

### Post by zhenya on 2008-09-18
Thank you for your assistance.  I've tried doing what you recommend, and the array was assembled, but I cannot mount it.  I get:
```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I'm not sure how this applies (although I'm sure it does) but prior to your post I tried re-creating the array, as I found a number of posts here and through google indicating that this would work.  I ran ```
sudo mdadm --create --verbose /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sdc1 /dev/sdd1 /dev/sdb1 /dev/sda1
```

Prior to that I had checked the order by examining one of the disks.

Any further suggestions?

---

### Post by zhenya on 2008-09-18
Ok, more follow up.  I checked the original order of the array by looking at /var/log/messages.  In there I found the original order of the 4 drive array: ```
Sep 14 08:37:33 fileserver kernel: [  109.596927]  disk 0, o:1, dev:sdc1
Sep 14 08:37:33 fileserver kernel: [  109.596937]  disk 1, o:1, dev:sdd1
Sep 14 08:37:33 fileserver kernel: [  109.596947]  disk 2, o:1, dev:sda1
Sep 14 08:37:33 fileserver kernel: [  109.596956]  disk 3, o:1, dev:sdb1

```

and then was able to assemble the array: ```
 sudo mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdd1 /dev/sda1 /dev/sdb1
mdadm: /dev/md0 has been started with 4 drives.
```

However I am unable to mount the /dev/md0 array:```
zhenya@fileserver:/var/log$ sudo mount /dev/md0 /mnt/Storage/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The output of dmesg | tail:```
zhenya@fileserver:/var/log$ dmesg | tail
[ 7266.779941] raid5: allocated 4204kB for md0
[ 7266.779961] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
[ 7266.779974] RAID5 conf printout:
[ 7266.779983]  --- rd:4 wd:4
[ 7266.779995]  disk 0, o:1, dev:sdc1
[ 7266.780006]  disk 1, o:1, dev:sdd1
[ 7266.780017]  disk 2, o:1, dev:sda1
[ 7266.780027]  disk 3, o:1, dev:sdb1
[ 7270.513615] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap for group 3968 not in group (block 134217728)!
[ 7270.651150] EXT3-fs: group descriptors corrupted!

```


I don't know where to go from here.  Can anyone help???

---

### Post by zhenya on 2008-09-19
Bump for more assistance.  Am I screwed?  #-o

---

### Post by fjgaude on 2008-09-19
I'm not sure but did you ever after creating the array install a filesystem, ext3?

---

