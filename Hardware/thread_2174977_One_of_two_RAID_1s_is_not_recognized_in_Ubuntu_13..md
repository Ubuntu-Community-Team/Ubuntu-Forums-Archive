---
title: "One of two RAID 1s is not recognized in Ubuntu 13.04"
date: 2013-09-17
forum: Hardware
---

### Post by ht3k on 2013-09-17
[SIZE=2][FONT=arial][COLOR=#333333]I have a 256GB SSD (Ubuntu/Win8), and two 1TB drives in RAID 1.[/COLOR]
[COLOR=#333333]The problem is that I just recently added another two drives that are 4TB in RAID 1 but they aren't detected in Ubuntu as one drive but separate.[/COLOR]
[COLOR=#333333]I know it works because Windows detected my new 4TB RAID 1 just fine, here's a screenshot via one of the raid disk utilities that came with my motherboard (fakeraid).[/COLOR]
[http://i.stack.imgur.com/XU0LD.png](http://i.stack.imgur.com/XU0LD.png)

```


    Disk /dev/sda: 256.1 GB, 256060514304 bytes
    255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x0a7f44fd
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1               1   500118191   250059095+  ee  GPT
    
    WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.
    
    
    Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes
    255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sdb doesn't contain a valid partition table
    
    WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.
    
    
    Disk /dev/sdc: 4000.8 GB, 4000787030016 bytes
    255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sdc doesn't contain a valid partition table
    
    WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.
    
    
    Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
    255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sdd doesn't contain a valid partition table
    
    WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.
    
    
    Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
    255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sde doesn't contain a valid partition table
    
    WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/ddf1_TeraRAID'! The util fdisk doesn't support GPT. Use GNU Parted.
    
    
    Disk /dev/mapper/ddf1_TeraRAID: 1000.1 GB, 1000120999936 bytes
    255 heads, 63 sectors/track, 121591 cylinders, total 1953361328 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
                        Device Boot      Start         End      Blocks   Id  System
    /dev/mapper/ddf1_TeraRAID1               1  1953361327   976680663+  ee  GPT
    
    Disk /dev/mapper/ddf1_TeraRAID1: 134 MB, 134217728 bytes
    255 heads, 63 sectors/track, 16 cylinders, total 262144 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000040
    
    Disk /dev/mapper/ddf1_TeraRAID1 doesn't contain a valid partition table
    
    Disk /dev/mapper/ddf1_TeraRAID2: 998.9 GB, 998911246336 bytes
    255 heads, 63 sectors/track, 121444 cylinders, total 1950998528 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x73736572
    
    This doesn't look like a partition table
    Probably you selected the wrong device.
    
                          Device Boot      Start         End      Blocks   Id  System
    /dev/mapper/ddf1_TeraRAID2p1      1920221984  3736432267   908105142   72  Unknown
    /dev/mapper/ddf1_TeraRAID2p2   ?  1936028192  3889681299   976826554   6c  Unknown
    /dev/mapper/ddf1_TeraRAID2p3   ?           0           0           0    0  Empty
    /dev/mapper/ddf1_TeraRAID2p4        27722122    27722568         223+   0  Empty
    
    Disk /dev/mapper/ddf1_TeraRAID3: 1073 MB, 1073741824 bytes
    255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    Disk /dev/mapper/ddf1_TeraRAID3 doesn't contain a valid partition table

```
[/FONT][/SIZE][SIZE=2][FONT=arial]

**[SIZE=4]blkid[/SIZE]**
```

    /dev/sda1: LABEL="Recovery" UUID="0AE412DFE412CD37" TYPE="ntfs" 
    /dev/sda2: UUID="0613-84B4" TYPE="vfat" 
    /dev/sda4: UUID="3A1214B712147A59" TYPE="ntfs" 
    /dev/sda5: UUID="dbb033df-b455-41c5-a050-d6aa816462a1" TYPE="ext4" 
    /dev/sda6: UUID="8577fdea-9aef-4789-b62e-86100019d2e1" TYPE="swap" 
    /dev/sdd: TYPE="ddf_raid_member" 
    /dev/sde: TYPE="ddf_raid_member" 
    /dev/mapper/ddf1_TeraRAID2: LABEL="TeraRAID" UUID="202E91BF2E918E82" TYPE="ntfs" 
    /dev/mapper/ddf1_TeraRAID3: LABEL="RandomStuff" UUID="00eea61f-86f3-46fb-bd66-07da8355a2f4" TYPE="ext4"

```

My 4TB drives `/dev/sdb` and `/dev/sdc` should be recognized as `ddf_raid_member` but they're nowhere to be found here...


**[SIZE=4]blkid -p /dev/sdb[/SIZE]**
**this command gives no output**


[B][SIZE=4]dmraid -rvv /dev/sdb
[/SIZE][/B]
```

    NOTICE: /dev/sdb: asr     discovering
    NOTICE: /dev/sdb: ddf1    discovering
    NOTICE: /dev/sdb: hpt37x  discovering
    NOTICE: /dev/sdb: hpt45x  discovering
    NOTICE: /dev/sdb: isw     discovering
    NOTICE: /dev/sdb: jmicron discovering
    NOTICE: /dev/sdb: lsi     discovering
    NOTICE: /dev/sdb: nvidia  discovering
    NOTICE: /dev/sdb: pdc     discovering
    NOTICE: /dev/sdb: sil     discovering
    NOTICE: /dev/sdb: via     discovering
    no raid disks and with names: "/dev/sdb"

```
**[SIZE=4]fstab[/SIZE]**
```

    # /etc/fstab: static file system information.
    #
    # Use 'blkid' to print the universally unique identifier for a
    # device; this may be used with UUID= as a more robust way to name devices
    # that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    # / was on /dev/sda5 during installation
    UUID=dbb033df-b455-41c5-a050-d6aa816462a1 /               ext4    errors=remount-ro 0       1
    # /boot/efi was on /dev/sda2 during installation
    #UUID=0613-84B4  /boot/efi       vfat    defaults        0       1
    # swap was on /dev/sda6 during installation
    UUID=8577fdea-9aef-4789-b62e-86100019d2e1 none            swap    sw              0       0
    UUID=0613-84B4  /boot/efi   vfat    defaults    0   1
```


How can I get Ubuntu to recognize my newly made 4TB RAID 1?[/FONT][/SIZE]

---

