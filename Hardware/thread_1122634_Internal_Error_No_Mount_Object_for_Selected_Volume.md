---
title: "Internal Error: No Mount Object for Selected Volume"
date: 2009-04-11
forum: Hardware
---

### Post by xcusmwah on 2009-04-11
I have several hard drives which when accessed via Nautilus 2.24.1 gives me an "Internal Error: No Mount Object for Selected Volume" error.  I click OK and then am able to access the drive upon double clicking the drive icon again.  My question is how can I prevent that error from showing so I don't have to access the drive two times in order to access my data?  Thank you

---

### Post by taurus on 2009-04-11
Do you want to have those drives mounted automatically each time you boot Ubuntu?  You can add entries for those drives in /etc/fstab if that is what you want.

---

### Post by ajgreeny on 2009-04-11
Or if you prefer to not have all partitions/disks mounted at boot time, I suggest you use the panel applet "Disk Mounter"  It puts a small icon for each partition on the panel and when you click it you get the option to mount or unmount, depending on its current stare.  I love it, but I think I'm odd and don't like all my other partitions mounted at boot up.

---

### Post by xcusmwah on 2009-04-16
I would love to be able to mount the drives upon boot. How do I get it do do that?  Thanks!

---

### Post by taurus on 2009-04-16
Post the outputs of these commands from a terminal, running one line at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by xcusmwah on 2009-04-17
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0eca03ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           2       48641   390700800    f  W95 Ext'd (LBA)
/dev/sda5               2        7792    62581176    7  HPFS/NTFS
/dev/sda6            7793       13288    44146588+   7  HPFS/NTFS
/dev/sda7           13289       48641   283972941    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0d4cc13a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1     1938021   976762552+   7  HPFS/NTFS

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ce3c4b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35da35da

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdf: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000339ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        8666    69609613+  83  Linux
/dev/sdf2            8667        9039     2996122+   5  Extended
/dev/sdf5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdg: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05c18ccf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       18513   148705641    7  HPFS/NTFS
/dev/sdg2           18514       48641   242003160    f  W95 Ext'd (LBA)
/dev/sdg5           18514       48641   242003128+   7  HPFS/NTFS

Disk /dev/sdh: 1994 MB, 1994227200 bytes
4 heads, 16 sectors/track, 60858 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x540f4c83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       60859     1947479+   e  W95 FAT16 (LBA)

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001    c  W95 FAT32 (LBA)

Disk /dev/sdj: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       91201   732572001    7  HPFS/NTFS


***************************************************

/dev/sda1: UUID="60BC59F8BC59C964" LABEL="MP3" TYPE="ntfs" 
/dev/sdb1: UUID="03ec4c96-b908-4a31-9f37-22703cb7ec52" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc1: UUID="44E08D11E08D0A7E" LABEL="Videos 2" TYPE="ntfs" 
/dev/sdd1: UUID="60BC59F8BC59C964" LABEL="MP3" TYPE="ntfs" 
/dev/sdd5: UUID="01C741B2B1E7EFA0" LABEL="Movies 2" TYPE="ntfs" 
/dev/sde6: UUID="3C4CB4B04CB465F4" LABEL="Our Documents" TYPE="ntfs" 
/dev/sde7: UUID="98F4CE1AF4CDFB10" LABEL="MMA, Wrestling, Boxing" TYPE="ntfs" 
/dev/sdf1: UUID="08586b6d-3fbd-4fc4-aa66-76db0c52b3fa" TYPE="ext3" 
/dev/sda5: UUID="1638BD6738BD4691" LABEL="Pictures" TYPE="ntfs" 
/dev/sda6: UUID="3C4CB4B04CB465F4" LABEL="Our Documents" TYPE="ntfs" 
/dev/sda7: UUID="98F4CE1AF4CDFB10" LABEL="MMA, Wrestling, Boxing" TYPE="ntfs" 
/dev/sde1: UUID="01C7B5D7ECFF5120" LABEL="Vidcasts" TYPE="ntfs" 
/dev/sdf5: TYPE="swap" UUID="a79dd859-904f-63a2-4e26-27430c5de2b2" 
/dev/sdg1: UUID="01C741B2AFAD41E0" LABEL="Home Videos" TYPE="ntfs" 
/dev/sdh1: SEC_TYPE="msdos" UUID="5AEA-873E" TYPE="vfat" 
/dev/sdi1: LABEL="MMA&EBOOKS" UUID="B246-A751" TYPE="vfat" 
/dev/sdi5: UUID="01C741B2B1E7EFA0" LABEL="Movies 2" TYPE="ntfs" 
/dev/sdg5: UUID="01C741B2B1E7EFA0" LABEL="Movies 2" TYPE="ntfs" 
/dev/sdj1: UUID="F0402BC1402B8D82" LABEL="Videos" TYPE="ntfs" 

***********************************************

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdf1 :
UUID=08586b6d-3fbd-4fc4-aa66-76db0c52b3fa / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdf5 :
UUID=a79dd859-904f-63a2-4e26-27430c5de2b2 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdc1 /media/Videos\0402 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda7 /media/MMA,\040Wrestling,\040Boxing ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda6 /media/Our\040Documents ntfs-3g defaults,locale=en_US.UTF-8 0 0


*****************************************

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdf1              66G   30G   34G  48% /
tmpfs                 758M     0  758M   0% /lib/init/rw
varrun                758M  228K  758M   1% /var/run
varlock               758M     0  758M   0% /var/lock
udev                  758M  2.9M  755M   1% /dev
tmpfs                 758M  580K  758M   1% /dev/shm
lrm                   758M  2.0M  756M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc1             932G  780G  153G  84% /media/Videos 2
/dev/sda7             271G   22G  250G   8% /media/MMA, Wrestling, Boxing
/dev/sda6              43G   30G   13G  70% /media/Our Documents
/dev/sdh1             1.9G  1.2M  1.9G   1% /media/disk
/dev/scd1             4.2M  4.2M     0 100% /media/U3 System
/dev/sdi1             932G  830G  103G  90% /media/MMA&EBOOKS
/dev/sdj1             699G  587G  112G  84% /media/Videos

---

### Post by taurus on 2009-04-17
Which partition are we talking here since you have a bunch of ntfs (and one vfat) partitions?  If it's the ntfs partition, then install ntfs-config and use it to configure that partition, having it mount automatically each time you boot.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by xcusmwah on 2009-04-18
Thank you very much, this worked great.

---

