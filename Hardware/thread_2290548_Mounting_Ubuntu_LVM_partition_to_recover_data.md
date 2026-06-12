---
title: "Mounting Ubuntu LVM partition to recover data"
date: 2015-08-13
forum: Hardware
---

### Post by lena-lueke on 2015-08-13
Hello everyone,

I have never posted in any forum so I am new to this but I hope you can help.
I searched and googled a lot but nothing I could find could resolve this. I think the solution might be very simple but since I dont understand partitions very well I am not seeing it.

My laptop broke due to a motherboard problem and I urgently need to recover my data from the harddrive.
It is a Dell XPS 13 and has Ubuntu 14.04 installed. The disk is a mSATA SSD 250GB.

What I did is put it into a mSATA to SATA adapter, put it in a docking station and plugged it in to a Sony Vaio with Ubuntu 14.04 installed.

The disk has 2 partitions a 255MB ext2 which mounts without a problem and a 240GB lvm2 which is recognized but does not mount.

I tried mounting as root but that gave me this error: 

mount: unknown filesystem type 'LVM2_member'

I tried making a disk image of the partition (I don't know if that made any sense)

I also tried booting the sony vaio from the hard disk in the docking station but that did not work.

I don't know much about this and I am scared of accidentally deleting anything.

Could you help me on where to start resolving this?

gparted is saying this:

```
lvm pvs --config "log{command_names=0}" --nosuffix --noheadings --separator , --units b -o vg_name,vg_attr,lv_name,lv_attr
  ubuntu-vg,wz--n-,root,-wi-ao---  ubuntu-vg,wz--n-,swap_1,-wi-ao---  ubuntu-vg,wz--n-,,
  Found duplicate PV my0zo7sBVzIz5Oe33S0HID4HD1s9qPdd: using /dev/sdb5 not /dev/loop0  Unable to find /dev/sdb5 in volume group ubuntu-vg
An error occurred reading LVM2 configuration!Some or all of the details might be missing or incorrect.You should NOT modify any LVM2 PV partitions.
```

below output of blkid, 

```

/dev/sda1: UUID="d893050f-c2e4-4cda-b9cb-c017962e9098" TYPE="ext2" 
/dev/sda5: UUID="qZXmoY-TlFv-XevR-MuyO-dD1b-4RMk-LZY11i" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="0d6073c7-a133-498f-b957-f37cf4d09279" TYPE="ext4" 
/dev/mapper/ubuntu--vg-swap_1: UUID="7eceacbe-b1b2-4f9b-ac5f-b04eab46c83f" TYPE="swap"

```

output of lsblk

```

NAME                         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                            8:0    0 298,1G  0 disk 
&#9500;&#9472;sda1                         8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                         8:2    0     1K  0 part 
&#9492;&#9472;sda5                         8:5    0 297,9G  0 part 
  &#9500;&#9472;ubuntu--vg-root (dm-0)   252:0    0 292,2G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 (dm-1) 252:1    0   5,7G  0 lvm  [SWAP]
sdb                            8:16   0 238,5G  0 disk 
&#9500;&#9472;sdb1                         8:17   0   243M  0 part /media/gebir/b9223840-dcb
&#9500;&#9472;sdb2                         8:18   0     1K  0 part 
&#9492;&#9472;sdb5                         8:21   0 238,2G  0 part 
sr0                           11:0    1  1024M  0 rom  
loop0                          7:0    0 238,2G  0 loop 

```

---

### Post by TheFu on 2015-08-13
Plug the disk into a different computer that does NOT use UEFI to boot and it should work - at least enough to get the data you want out. 

If you boot a live-boot CD/flash drive, the mount command should be something like 
**sudo mount /dev/mapper/ubuntu--vg-root /mnt**  All the data will be under /mnt and available.  I didn't test this, so there might be a step missing, but I don't think so.

BTW - thanks for posting lsblk output. THAT answered the questions I had, so I didn't need to ask.

---

### Post by lena-lueke on 2015-08-13
Hi TheFu,

thank you so much for your answer! And sorry for the late reply.

The computer I plugged it in to is not using UEFI. 
I tried **sudo mount /dev/mapper/ubuntu--vg-root /mnt **but it only mounted the filesystem of the computer not the partition I need.

I think the partition I need to mount is in sdb5 but I am not sure.
Is there anything else I can do?

---

### Post by TheFu on 2015-08-13
Unplug the other drive in the test computer, leave just the one you want connected.
Or you could mount sdb5 if you like and it isn't already mounted.  Can't tell what that partition has without seeing **sudo parted -l** output. 

Sorry, I thought you said the disk with the data you wanted was using LVM?  sdb isn't using LVM - sda is.

---

### Post by weatherman2 on 2015-08-13
Sometimes LVM volumes need to be imported/activated before they can be seen (become "available") on a new system.  You might try this command:

```
sudo vgchange -a y.
```

then run vgdisplay and lvdisplay to see if your logical volumes are detected.

---

### Post by lena-lueke on 2015-08-13
Thank you for the answers!
I am almost certain that sdb5 is what I need. I thought sda is of the system of the system of the notebook I am using now to read the disk.

When I look at it in gparted I see that sda5 and sdb5 have the same file system and the same mount point "ubuntu-vg". 
Could this be a problem? Here is a screenshot

sda:
[ATTACH=CONFIG]263836[/ATTACH]
sdb:
[ATTACH=CONFIG]263837[/ATTACH]

Here is the sudo parted -l output:

```
Model: ATA ST9320423AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   320GB  320GB  extended
 5      257MB   320GB  320GB  logical                lvm




Model: Generic External (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   256GB  256GB  extended
 5      257MB   256GB  256GB  logical                lvm




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 314GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0,00B  314GB  314GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 6086MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0,00B  6086MB  6086MB  linux-swap(v1)

```

vgchange -a y:

  ```

Found duplicate PV my0zo7sBVzIz5Oe33S0HID4HD1s9qPdd: using /dev/sdb5 not /dev/loop0
  device-mapper: create ioctl on ubuntu--vg-root failed: Device or resource busy
  device-mapper: create ioctl on ubuntu--vg-swap_1 failed: Device or resource busy
  0 logical volume(s) in volume group "ubuntu-vg" now active
  2 logical volume(s) in volume group "ubuntu-vg" now active

```

vgdisplay:

```
 Found duplicate PV my0zo7sBVzIz5Oe33S0HID4HD1s9qPdd: using /dev/sdb5 not /dev/loop0
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               238,23 GiB
  PE Size               4,00 MiB
  Total PE              60988
  Alloc PE / Size       60987 / 238,23 GiB
  Free  PE / Size       1 / 4,00 MiB
  VG UUID               9sfRoO-d7dB-YcPW-2ZxR-l9AY-e3w5-vDzS0H
   
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               297,85 GiB
  PE Size               4,00 MiB
  Total PE              76249
  Alloc PE / Size       76245 / 297,83 GiB
  Free  PE / Size       4 / 16,00 MiB
  VG UUID               dTRd4E-BeV2-q6wc-gre6-iUta-imGc-qmN8fX

```

lvdisplay:

```
  Found duplicate PV my0zo7sBVzIz5Oe33S0HID4HD1s9qPdd: using /dev/sdb5 not /dev/loop0
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                Fg1jjg-eKto-7KNj-YMSQ-lWdt-E2xb-eXhQyj
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-08-11 19:58:09 +0200
  LV Status              NOT available
  LV Size                230,70 GiB
  Current LE             59060
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                UzxVQg-wB75-znGT-SLDu-YA2g-Q5JH-vlnxHv
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-08-11 19:58:10 +0200
  LV Status              NOT available
  LV Size                7,53 GiB
  Current LE             1927
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto

```
I imagine the duplicate found is the disk image I made before...
As far as I understand only the lv in sda are found(?)

---

### Post by weatherman2 on 2015-08-13
I'd guess that duplicate Volume Group names is causing your confusion.

You can rename your volume group, but it might be easier to boot a live USB instead and avoid the confusion in the first place.

[http://manpages.ubuntu.com/manpages/dapper/man8/vgrename.8lvm-10.html](http://manpages.ubuntu.com/manpages/dapper/man8/vgrename.8lvm-10.html)

---

### Post by lena-lueke on 2015-08-13
renaming the volume group did the trick.

Thank you so much weatherman2 and also TheFu!

I first tried the live cd but the same problem occurred so I unplugged the disk renamed the systems volume group with:

```
vgrename /dev/ubuntu-vg /dev/ubuntu-vg2
```

Plugged in the disk again and did:

```
vgchange -a y
```

which gave me:

```
2 logical volume(s) in volume group "ubuntu-vg" now active
2 logical volume(s) in volume group "ubuntu-vg2" now active

```

vgdisplay output:

```

LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                Fg1jjg-eKto-7KNj-YMSQ-lWdt-E2xb-eXhQyj
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-08-11 19:58:09 +0200
  LV Status              available
  # open                 0
  LV Size                230,70 GiB
  Current LE             59060
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                UzxVQg-wB75-znGT-SLDu-YA2g-Q5JH-vlnxHv
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-08-11 19:58:10 +0200
  LV Status              available
  # open                 0
  LV Size                7,53 GiB
  Current LE             1927
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg2/root
  LV Name                root
  VG Name                ubuntu-vg2
  LV UUID                52cCFK-MiL1-6epi-FFCR-sZzt-bC3L-9t9WJN
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-09-23 11:03:34 +0200
  LV Status              available
  # open                 1
  LV Size                292,16 GiB
  Current LE             74794
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg2/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg2
  LV UUID                PGyVfh-qVSn-EXsz-a12c-xWxN-E3g2-BWWx1S
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-09-23 11:03:35 +0200
  LV Status              available
  # open                 2
  LV Size                5,67 GiB
  Current LE             1451
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

```

then I mounted successfully with:

```
mount /dev/ubuntu-vg/root /mnt
```

Thanks again!

---

