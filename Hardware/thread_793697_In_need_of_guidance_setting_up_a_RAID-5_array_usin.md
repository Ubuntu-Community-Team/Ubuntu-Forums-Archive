---
title: "In need of guidance setting up a RAID-5 array using mdadm"
date: 2008-05-14
forum: Hardware
---

### Post by JHawk24821 on 2008-05-14
Please excuse my forum etiquette, I am a novice poster.  That being said, suggestions and corrections are welcome!

I have a single 150 GB SATA drive that holds both / and swap.  I have added 3 x 1TB SATA drives as a RAID-5 array that I would like to have mounted under /media/raid.  I am able to build the array, format it, and mount it, however I am running into two problems:

[LIST=1]
[*]After formatting and mounting, I can write to the array via the command line but not via the desktop's GUI.
[*]Rebooting is a mixed bag, usually resulting in the array not being mounted or (if I am really lucky) being completely missing.
[/LIST]

Below is the info that I think you'll need to at least get an understanding of what's going on.  Please let me know what other info I can provide.


**mdadm array creation command:**
```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1 --spare-devices=0 --force --verbose
```


**resulting array:**
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue May 13 21:31:46 2008
     Raid Level : raid5
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue May 13 21:32:19 2008
          State : active, resyncing
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 14% complete

           UUID : 6c66b9c9:299cfa08:1331431d:61610d45
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
```


**fstab:**
```
# /etc/fstab: static file system information.
#
# <file system>                                 <mount point>   <type>          <options>                       <dump>  <pass>
proc                                            /proc           proc            defaults                        0       0
UUID=5b0cd021-2d75-444b-b786-33b336df5ad4       /               ext3            relatime,errors=remount-ro      0       1
UUID=2c90d893-94fe-4660-b503-feae50918b72       none            swap            sw                              0       0
/dev/md0                                        /media/raid     auto		 defaults			 0       3
/dev/scd0                                       /media/cdrom0   udf,iso9660     user,noauto,exec,utf8           0       0
/dev/fd0                                        /media/floppy0  auto            rw,user,noauto,exec,utf8        0       0
```


**df -kh:**
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             133G   45G   82G  36% /
varrun                2.0G  112K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   80K  2.0G   1% /dev
devshm                2.0G  208K  2.0G   1% /dev/shm
lrm                   2.0G   43M  1.9G   3% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      133G   45G   82G  36% /home/jesse/.gvfs
/dev/md0              1.9T  196M  1.8T   1% /media/raid
```


**Permission on /media/raid**
```
drwxr-xr-x 3 root root 4.0K 2008-05-13 21:39 raid/
```


Thanks for your time!

- Jesse

---

### Post by JHawk24821 on 2008-05-15
bump

---

### Post by psusi on 2008-05-15
You will have to be more specific about what is wrong when you reboot.  The only thing out of the ordinary I see is that the raid directory is owned by root, so you don't have access to it.

---

### Post by JHawk24821 on 2008-05-15
I caught the permission error you mentioned last night, so that problem is behind me.  Also, I was able to reboot and have the array auto-mount!  It seems that the format of my /etc/mdadm/mdadm.conf was off and last night's tweaking fixed things up.  I will post the config's tonight and mark the thread resolved if everything looks good.

Thanks!

---

### Post by pancakelizard on 2008-05-28
I will be doing the same tonight (dependant on newegg delivery) and was wondering how did you change the root permissions for the raid so that the problem no longer occured.

Or, how do you make sure this does not occur in the first place?

Thanks.

---

### Post by JHawk24821 on 2008-05-28
When creating the mount point in /media, you have to use sudo which produces a directory owned by root.

```
sudo mkdir /media/raid_big
```

The problem was that when I mounted my array under these points, the root ownership caused issues.  I fixed it by changing the owner of /media/raid_big.

```
sudo chown jesse:jesse /media/raid_big
```

Give that a try if you run into problems.  Good luck!  :)

---

