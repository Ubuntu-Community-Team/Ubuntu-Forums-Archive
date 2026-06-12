---
title: "LVG not extending to all volumes"
date: 2015-08-16
forum: Hardware
---

### Post by Gridwalker on 2015-08-16
Hi there,

I upgraded to an SSD last year, cloning my existing OS installation from the old root drive because I didn't want to have to reconfigure everything from scratch. As the new SSD was 40gb larger than the original HDD, I chose to extend the root partition using a logical volume to take up the remaining space.

The "Physical View" in Ubuntu's LVM tool shows the root partition taking up the whole drive except a small portion in the middle that was assigned to a swap file by the original installation. 

[IMG]http://i.imgur.com/FSaegXm.png[/IMG]

The "Logical View" of the LVM also shows the root partition as a 107gb logical volume in 2 segments. Similarly, Gparted shows the root and swap partitions combined as a 111gb LVG. 

Unfortunately, the rest of the operating system does not agree. In every other application, the 2nd segment of the root partition is not recognised and only the first 74gb is displayed. This hasn't been a problem for the last year, but I have finally run out of space on root and I need to find a way of rectifying this issue.

Can anyone give me a layman's explanation of where I am going wrong and how to sort this out? This was the first time I had tried manually configuring LVG settings and I am damned if I can understand where it went wrong.

---

### Post by weatherman2 on 2015-08-16
Can you please run these commands and provide their output:

```

sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
df
sudo parted -l

```

---

### Post by Gridwalker on 2015-08-17
**sudo pvdisplay**
```
--- Physical volume ---
  PV Name               /dev/sdc5
  VG Name               ubuntu-vg
  PV Size               111.06 GiB / not usable 3.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              28431
  Free PE               0
  Allocated PE          28431
  PV UUID               QxMNJI-0a1m-heMK-OqhN-CoAp-JDDS-BiSHW8
```

**sudo vgdisplay**
```
 --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  19
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               111.06 GiB
  PE Size               4.00 MiB
  Total PE              28431
  Alloc PE / Size       28431 / 111.06 GiB
  Free  PE / Size       0 / 0   
  VG UUID               XhyZ06-rXtQ-8AYi-lqfL-XkF8-c5H5-MpMdPa

```

**sudo lvdisplay**
```
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                mUhD4w-yVgl-dnYw-sOxd-9Tit-KHXE-8cxH8U
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-05-12 18:44:58 +0100
  LV Status              available
  # open                 1
  LV Size                107.12 GiB
  Current LE             27423
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                odsLfb-kELV-1i72-ZjbR-NwF4-4Hkc-rgCwvy
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-05-12 18:44:59 +0100
  LV Status              available
  # open                 2
  LV Size                3.94 GiB
  Current LE             1008
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

```

**df**
```
Filesystem                   1K-blocks       Used  Available Use% Mounted on
udev                           6004244          0    6004244   0% /dev
tmpfs                          1210804      10084    1200720   1% /run
/dev/mapper/ubuntu--vg-root   72504624   63045460    5753104  92% /
tmpfs                          6054004      86588    5967416   2% /dev/shm
tmpfs                             5120          4       5116   1% /run/lock
tmpfs                          6054004          0    6054004   0% /sys/fs/cgroup
/dev/sdc1                       737262     393430     305793  57% /boot
/dev/md1                     153713700   69420440   76461964  48% /home
/dev/sdd1                   1922728752 1156836436  668200260  64% /media/gridwalker/Anguirus
/dev/md127                  5813844520 3958951724 1561869052  72% /media/gridwalker/Megalon
tmpfs                          1210804         64    1210740   1% /run/user/1000

```

**sudo parted -l**
```
Model: ATA MAXTOR 6L080J4 (scsi)
Disk /dev/sda: 80.1GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  80.0GB  80.0GB  ext4


Model: ATA MAXTOR STM380215 (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  80.0GB  80.0GB  ext4


Model: ATA INTEL SSDSA2BW12 (scsi)
Disk /dev/sdc: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  780MB  779MB  primary   ext2         boot
 2      780MB   120GB  119GB  extended
 5      781MB   120GB  119GB  logical                lvm


Model: ATA ST32000542AS (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB  ext4


Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sde: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB  ext4


Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdf: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 115GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  115GB  115GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4228MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  4228MB  4228MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  160GB  160GB  ext4


Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sdg: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB  ext4


Model: ATA Hitachi HDS72302 (scsi)
Disk /dev/sdh: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md127: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  6001GB  6001GB  ext4

```

For clarity, this box originally started out with 2x80gb IDE drives (SDA + SDB). I then upgraded to a 120gb SSD (SDC) and configured the 2 IDE drives as a RAID 0 array (MD1), which I mounted as my home folder. 

I subsequently added a 2tb SATA2 HDD (SDD) for general storage, followed by 4x2tb SATA3 HDDs (SDE, F, G & H) configured as a RAID5 array (MD127) that I set up so the machine could be used as a media centre. 

Part of the reason why I am running so low on space is that Plex stores all media server metadata on the Root drive, which now totals approx 40gb in itself. I could hack a workaround by duplicating that folder elsewhere and replacing the original with a symbolic link, but I would rather unlock the extra space on my SSD.

---

### Post by weatherman2 on 2015-08-17
OK, I assume you followed something like this and used the lvextend command to enlarge the logical volume:

[http://www.linuxtechi.com/extend-lvm-partitions/](http://www.linuxtechi.com/extend-lvm-partitions/)

But did you also do resize2fs ?

You'd have to do this for your root partition for a live Linux boot (e.g. live USB) - can't resize the root file system while it is running...

I'm assuming you have a backup of your root partition as well - as you know, these commands can be dangerous if done the wrong way.

I'd move the Plex file anyway with a symlink to some other partition, even after you enlarge the fs.

---

