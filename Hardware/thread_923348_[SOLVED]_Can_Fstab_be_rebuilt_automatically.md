---
title: "[SOLVED] Can Fstab be rebuilt automatically"
date: 2008-09-18
forum: Hardware
---

### Post by randogauci on 2008-09-18
I am a newbie and I installed Ubuntu 8.04 64 on AMD 64 and everything just worked! I could brows all my drives and partitions including NTFS. After several updates/upgrades I could no longer mount my other drives or partitions. Even inserting USB sticks, they are shown in "Computer" but cannot be mounted. Is there a way of getting the system to remount everything from scratch as during the Install process???
At present /dev/sda1, /dev/sdc1, and cdrom cannot be mounted!

So far I had tried many times to edit the fstab and had to revert back each time as no differences occurred. I have followed several threads and this is how my system looks:-

ron@AMD-UB804:~$ sudo blkid
sudo: unable to resolve host AMD-UB804
[sudo] password for ron: 
/dev/sda1: UUID="C2083CA5083C99FD" LABEL="Sata-1-DATA" TYPE="ntfs" 
/dev/sda5: UUID="C270C56970C5652F" LABEL="SATA-2-Downloads" TYPE="ntfs" 
/dev/sdb1: UUID="E6688D1C688CEC9D" LABEL="Music-Rons" TYPE="ntfs" 
/dev/hda1: UUID="65cd7909-303d-43d8-adf6-99fc726830e7" TYPE="ext2" 
/dev/hda3: TYPE="swap" UUID="d7066879-bc4c-46d7-bca3-1bfd3f09272a" 
/dev/hda4: UUID="4a38573f-016f-4ed3-bf01-3756cb8eb735" TYPE="ext3" 
/dev/hda5: UUID="afbab3ae-46a9-4e02-9b26-4b725285c766" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="RONGAUCI" UUID="F7DE-F860" TYPE="vfat" 

ron@AMD-UB804:~$ sudo fdisk -l
sudo: unable to resolve host AMD-UB804

Disk /dev/sda: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x81c04f4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      193016    97280032+   7  HPFS/NTFS
/dev/sda2          193017      387618    98079408    5  Extended
/dev/sda5          193017      387618    98079376+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x737e737e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8a3b8a3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          12       96358+  83  Linux
/dev/hda2            2991        9964    56018655    f  W95 Ext'd (LBA)
/dev/hda3              13         620     4883760   82  Linux swap / Solaris
/dev/hda4             621        2990    19037025   83  Linux
/dev/hda5            2991        9964    56018623+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1041 MB, 1041235456 bytes
255 heads, 63 sectors/track, 126 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         126     1012063+   6  FAT16

ron@AMD-UB804:~$ ls /dev/disk/* -lah
/dev/disk/by-id:
total 0
drwxr-xr-x 2 root root 540 2008-09-18 18:37 .
drwxr-xr-x 6 root root 120 2008-09-18 18:37 ..
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 ata-HL-DT-ST_DVDRAM_GSA-4163B_K06545F4626 -> ../../hdb
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E -> ../../hda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part1 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part2 -> ../../hda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part3 -> ../../hda3
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part4 -> ../../hda4
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part5 -> ../../hda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 ata-ST3200822A_3LJ2DRA0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-ST3200822A_3LJ2DRA0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 ata-ST3200822AS_4LJ15MTT -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-ST3200822AS_4LJ15MTT-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-ST3200822AS_4LJ15MTT-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-ST3200822AS_4LJ15MTT-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 scsi-1ATA_ST3200822A_3LJ2DRA0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 scsi-1ATA_ST3200822A_3LJ2DRA0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 scsi-1ATA_ST3200822AS_4LJ15MTT -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 scsi-1ATA_ST3200822AS_4LJ15MTT-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 scsi-1ATA_ST3200822AS_4LJ15MTT-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 scsi-1ATA_ST3200822AS_4LJ15MTT-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-_Flash_Disk_184002908432-0:0 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 usb-_Flash_Disk_184002908432-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-Generic_USB_CF_Reader_058F312D81B-0:1 -> ../../sde
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-Generic_USB_MS_Reader_058F312D81B-0:3 -> ../../sdg
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-Generic_USB_SD_Reader_058F312D81B-0:0 -> ../../sdd
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-Generic_USB_SM_Reader_058F312D81B-0:2 -> ../../sdf

/dev/disk/by-label:
total 0
drwxr-xr-x 2 root root 120 2008-09-18 18:37 .
drwxr-xr-x 6 root root 120 2008-09-18 18:37 ..
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 Music-Rons -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 RONGAUCI -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 Sata-1-DATA -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 SATA-2-Downloads -> ../../sda5

/dev/disk/by-path:
total 0
drwxr-xr-x 2 root root 420 2008-09-18 18:37 .
drwxr-xr-x 6 root root 120 2008-09-18 18:37 ..
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:11.0-scsi-2:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:11.0-scsi-2:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:11.0-scsi-2:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:11.0-scsi-2:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:1.4:1.0-scsi-0:0:0:0 -> ../../sdd
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:1.4:1.0-scsi-0:0:0:1 -> ../../sde
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:1.4:1.0-scsi-0:0:0:2 -> ../../sdf
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:1.4:1.0-scsi-0:0:0:3 -> ../../sdg
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:4:1.0-scsi-0:0:0:0 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:13.2-usb-0:4:1.0-scsi-0:0:0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0 -> ../../hda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part1 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part2 -> ../../hda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part3 -> ../../hda3
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part4 -> ../../hda4
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part5 -> ../../hda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:14.1-ide-0:1 -> ../../hdb
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:03:07.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:03:07.0-scsi-0:0:0:0-part1 -> ../../sdb1

/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 200 2008-09-18 18:37 .
drwxr-xr-x 6 root root 120 2008-09-18 18:37 ..
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 4a38573f-016f-4ed3-bf01-3756cb8eb735 -> ../../hda4
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 65cd7909-303d-43d8-adf6-99fc726830e7 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 afbab3ae-46a9-4e02-9b26-4b725285c766 -> ../../hda5
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 C2083CA5083C99FD -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 C270C56970C5652F -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 d7066879-bc4c-46d7-bca3-1bfd3f09272a -> ../../hda3
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 E6688D1C688CEC9D -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 F7DE-F860 -> ../../sdc1
ron@AMD-UB804:~$ sudo blkid
sudo: unable to resolve host AMD-UB804
[sudo] password for ron: 
/dev/sda1: UUID="C2083CA5083C99FD" LABEL="Sata-1-DATA" TYPE="ntfs" 
/dev/sda5: UUID="C270C56970C5652F" LABEL="SATA-2-Downloads" TYPE="ntfs" 
/dev/sdb1: UUID="E6688D1C688CEC9D" LABEL="Music-Rons" TYPE="ntfs" 
/dev/hda1: UUID="65cd7909-303d-43d8-adf6-99fc726830e7" TYPE="ext2" 
/dev/hda3: TYPE="swap" UUID="d7066879-bc4c-46d7-bca3-1bfd3f09272a" 
/dev/hda4: UUID="4a38573f-016f-4ed3-bf01-3756cb8eb735" TYPE="ext3" 
/dev/hda5: UUID="afbab3ae-46a9-4e02-9b26-4b725285c766" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="RONGAUCI" UUID="F7DE-F860" TYPE="vfat" 

ron@AMD-UB804:~$ sudo fdisk -l
sudo: unable to resolve host AMD-UB804

Disk /dev/sda: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x81c04f4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      193016    97280032+   7  HPFS/NTFS
/dev/sda2          193017      387618    98079408    5  Extended
/dev/sda5          193017      387618    98079376+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x737e737e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8a3b8a3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          12       96358+  83  Linux
/dev/hda2            2991        9964    56018655    f  W95 Ext'd (LBA)
/dev/hda3              13         620     4883760   82  Linux swap / Solaris
/dev/hda4             621        2990    19037025   83  Linux
/dev/hda5            2991        9964    56018623+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1041 MB, 1041235456 bytes
255 heads, 63 sectors/track, 126 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         126     1012063+   6  FAT16

ron@AMD-UB804:~$ ls /dev/disk/* -lah
/dev/disk/by-id:
total 0
drwxr-xr-x 2 root root 540 2008-09-18 18:37 .
drwxr-xr-x 6 root root 120 2008-09-18 18:37 ..
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 ata-HL-DT-ST_DVDRAM_GSA-4163B_K06545F4626 -> ../../hdb
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E -> ../../hda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part1 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part2 -> ../../hda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part3 -> ../../hda3
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part4 -> ../../hda4
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-Maxtor_6Y080L0_Y3LFSA6E-part5 -> ../../hda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 ata-ST3200822A_3LJ2DRA0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-ST3200822A_3LJ2DRA0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 ata-ST3200822AS_4LJ15MTT -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-ST3200822AS_4LJ15MTT-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-ST3200822AS_4LJ15MTT-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 ata-ST3200822AS_4LJ15MTT-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 scsi-1ATA_ST3200822A_3LJ2DRA0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 scsi-1ATA_ST3200822A_3LJ2DRA0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 scsi-1ATA_ST3200822AS_4LJ15MTT -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 scsi-1ATA_ST3200822AS_4LJ15MTT-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 scsi-1ATA_ST3200822AS_4LJ15MTT-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 scsi-1ATA_ST3200822AS_4LJ15MTT-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-_Flash_Disk_184002908432-0:0 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 usb-_Flash_Disk_184002908432-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-Generic_USB_CF_Reader_058F312D81B-0:1 -> ../../sde
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-Generic_USB_MS_Reader_058F312D81B-0:3 -> ../../sdg
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-Generic_USB_SD_Reader_058F312D81B-0:0 -> ../../sdd
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 usb-Generic_USB_SM_Reader_058F312D81B-0:2 -> ../../sdf

/dev/disk/by-label:
total 0
drwxr-xr-x 2 root root 120 2008-09-18 18:37 .
drwxr-xr-x 6 root root 120 2008-09-18 18:37 ..
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 Music-Rons -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 RONGAUCI -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 Sata-1-DATA -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 SATA-2-Downloads -> ../../sda5

/dev/disk/by-path:
total 0
drwxr-xr-x 2 root root 420 2008-09-18 18:37 .
drwxr-xr-x 6 root root 120 2008-09-18 18:37 ..
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:11.0-scsi-2:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:11.0-scsi-2:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:11.0-scsi-2:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:11.0-scsi-2:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:1.4:1.0-scsi-0:0:0:0 -> ../../sdd
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:1.4:1.0-scsi-0:0:0:1 -> ../../sde
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:1.4:1.0-scsi-0:0:0:2 -> ../../sdf
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:1.4:1.0-scsi-0:0:0:3 -> ../../sdg
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:13.2-usb-0:4:1.0-scsi-0:0:0:0 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:13.2-usb-0:4:1.0-scsi-0:0:0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0 -> ../../hda
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part1 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part2 -> ../../hda2
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part3 -> ../../hda3
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part4 -> ../../hda4
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:00:14.1-ide-0:0-part5 -> ../../hda5
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:00:14.1-ide-0:1 -> ../../hdb
lrwxrwxrwx 1 root root   9 2008-09-18 18:37 pci-0000:03:07.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 pci-0000:03:07.0-scsi-0:0:0:0-part1 -> ../../sdb1

/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 200 2008-09-18 18:37 .
drwxr-xr-x 6 root root 120 2008-09-18 18:37 ..
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 4a38573f-016f-4ed3-bf01-3756cb8eb735 -> ../../hda4
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 65cd7909-303d-43d8-adf6-99fc726830e7 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 afbab3ae-46a9-4e02-9b26-4b725285c766 -> ../../hda5
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 C2083CA5083C99FD -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 C270C56970C5652F -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 d7066879-bc4c-46d7-bca3-1bfd3f09272a -> ../../hda3
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 E6688D1C688CEC9D -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-09-18 18:37 F7DE-F860 -> ../../sdc1

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb4
UUID=4a38573f-016f-4ed3-bf01-3756cb8eb735 /               ext3    relatime,errors=remount-ro 0       1
/dev/hdb5
UUID=afbab3ae-46a9-4e02-9b26-4b725285c766 /home           ext3    relatime        0       2
/dev/hdb3
UUID=d7066879-bc4c-46d7-bca3-1bfd3f09272a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs rw,user,fmask=0111,dmask=0000 0 0
/dev/sda5 /media/sda5 ntfs rw,user,fmask=0111,dmask=0000 0 0
/dev/sdb1 /media/sdb1 ntfs rw,user,fmask=0111,dmask=0000 0 0

ron@AMD-UB804:~$ sudo bash diskmounter
sudo: unable to resolve host AMD-UB804
By default the disks will be writable only by root and
Ron Gauci (ron)
Do you want to make the disk writable by all users instead? (y/n)
y
As of Ubuntu 6.04 (Dapper Drake) there is slightly more NTFS writing support
through a very experimental NTFS FUSE module. Using this seems to work but
is NOT recommended. Do you want to use this? [no] y
Not enabling experimental NTFS write support
Ignoring /dev/sda1 - already in /etc/fstab
Ignoring /dev/sda5 - already in /etc/fstab
Ignoring /dev/sdb1 - already in /etc/fstab
No usable windows/mac partitions found





Hope there is enough info. Any help would be appreciated.

---

### Post by IntuitiveNipple on 2008-09-18
First a minor issue, removing the warning
```

sudo: unable to resolve host AMD-UB804

```
This happens when the name of the PC is not resolved by look-up.

There should be an entry in the local host name resolution file that defines all names for the local PC on the internal loop-back network. I'd expect it to have entries looking something like this (there will be more lines, but these are the important ones):
```

cat /etc/hosts

127.0.0.1 localhost
127.0.1.1 AMD-UB804

```

If for 127.0.1.1 the name of the PC is missing add it. This command should do that for you:
```

sudo sed -i -e 's/^\(127\.0\.1\.1.*\)/\1 AMD-UB804/g' /etc/hosts

```
If there is no entry for 127.0.1.1 add it:
```

echo "127.0.1.1 AMD-UB804" | sudo tee -a /etc/hosts

```

The main problem, if you copied the contents of /etc/fstab accurately is that it is badly formatted. There are missing comment markers in front of the device names. It should look more like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb4
UUID=4a38573f-016f-4ed3-bf01-3756cb8eb735 / ext3 relatime,errors=remount-ro 0 1
#/dev/hdb5
UUID=afbab3ae-46a9-4e02-9b26-4b725285c766 /home ext3 relatime 0 2
# /dev/hdb3
UUID=d7066879-bc4c-46d7-bca3-1bfd3f09272a none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

```
The removable devices are usually not entered in the fstab since the auto-mounter will use the labels of the devices to mount them. For example, here is the *before* on this system:
```

$ ls /media

cdrom  cdrom0  disk2  mobile120  mobile40

```
... and *after* plugging in a USB memory stick:
```

$ ls /media

casper-rw  cdrom  cdrom0  disk2  mobile120  mobile40  ubuntu

```
If the /media directory lists directories with names (labels) of devices when they aren't connected it won't hurt to delete them (although so far as I know it also shouldn't cause it to fail). If they remain when the associated devices are disconnected it is possible to write data to the directory accidentally, thinking the device is mounted. In that case the data is just written to the root partition.

Restart the PC.
[list=1]
[*] Press **Esc**ape to get to the GrUB menu.
[*] Select the kernel entry you wish to start.
[*] Press **e** to edit it.
[*] Move the highlight to the line beginning "**kernel**"
[*] Press **e** to edit it.
[*] Use the back-space key to delete "quiet splash" from the end of the line.
[*] Press **Enter** to return to the previous menu.
[*] Press **b** to boot the system with the revised kernel options.
[/list]
You will now see the system reporting everything it does during start-up rather than it being hidden behind the splash-screen. At some point you should see mention of checking and mouting the disks. If there is anything wrong with the contents of /etc/fstab there will be warnings - make a note and deal with them once the system has started.

Once you're sure there are no errors in fstab you can move on with confidence to sort out the removable device mounting issues - which may have been solved by the previous step, too.

---

### Post by randogauci on 2008-09-19
> **IntuitiveNipple said:**
> First a minor issue, removing the warning
```

sudo: unable to resolve host AMD-UB804

```
This happens when the name of the PC is not resolved by look-up.

There should be an entry in the local host name resolution file that defines all names for the local PC on the internal loop-back network. I'd expect it to have entries looking something like this (there will be more lines, but these are the important ones):
```

cat /etc/hosts

127.0.0.1 localhost
127.0.1.1 AMD-UB804

```

If for 127.0.1.1 the name of the PC is missing add it. This command should do that for you:
```

sudo sed -i -e 's/^\(127\.0\.1\.1.*\)/\1 AMD-UB804/g' /etc/hosts

```
If there is no entry for 127.0.1.1 add it:
```

echo "127.0.1.1 AMD-UB804" | sudo tee -a /etc/hosts

```

The main problem, if you copied the contents of /etc/fstab accurately is that it is badly formatted. There are missing comment markers in front of the device names. It should look more like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb4
UUID=4a38573f-016f-4ed3-bf01-3756cb8eb735 / ext3 relatime,errors=remount-ro 0 1
#/dev/hdb5
UUID=afbab3ae-46a9-4e02-9b26-4b725285c766 /home ext3 relatime 0 2
# /dev/hdb3
UUID=d7066879-bc4c-46d7-bca3-1bfd3f09272a none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

```
The removable devices are usually not entered in the fstab since the auto-mounter will use the labels of the devices to mount them. For example, here is the *before* on this system:
```

$ ls /media

cdrom  cdrom0  disk2  mobile120  mobile40

```
... and *after* plugging in a USB memory stick:
```

$ ls /media

casper-rw  cdrom  cdrom0  disk2  mobile120  mobile40  ubuntu

```
If the /media directory lists directories with names (labels) of devices when they aren't connected it won't hurt to delete them (although so far as I know it also shouldn't cause it to fail). If they remain when the associated devices are disconnected it is possible to write data to the directory accidentally, thinking the device is mounted. In that case the data is just written to the root partition.

Restart the PC.
[list=1]
[*] Press **Esc**ape to get to the GrUB menu.
[*] Select the kernel entry you wish to start.
[*] Press **e** to edit it.
[*] Move the highlight to the line beginning "**kernel**"
[*] Press **e** to edit it.
[*] Use the back-space key to delete "quiet splash" from the end of the line.
[*] Press **Enter** to return to the previous menu.
[*] Press **b** to boot the system with the revised kernel options.
[/list]
You will now see the system reporting everything it does during start-up rather than it being hidden behind the splash-screen. At some point you should see mention of checking and mouting the disks. If there is anything wrong with the contents of /etc/fstab there will be warnings - make a note and deal with them once the system has started.

Once you're sure there are no errors in fstab you can move on with confidence to sort out the removable device mounting issues - which may have been solved by the previous step, too.
Hi TJ,
Thanks for that. I have done some of what you suggested and it did work. I am traveling around Australia at present and we don't always get Internet connection so this might take me a while to get right. At least the computer is usable!
Thanks again
Ron

---

### Post by randogauci on 2008-09-19
Hi again,
Thanks, everything is working OK. I edited the fstab and removed the last three lines, then ran diskmounter again and everything is now OK!
Regards
Ron

---

