---
title: "GRUB disappear after adding 4TB Hard drive in dual boot ubuntu 13.10/windows 7"
date: 2014-03-25
forum: Hardware
---

### Post by dodoking on 2014-03-25
I recently bought a new Hard drive 4TB to use for back up how ever after adding the hard-drive grub disappears 

and windows 7 boots right away 

both ubuntu and windows are installed on 500GB hdd divided into two partitions

when assigning a letter to the 4TB hard-drive set as GPT disk to have access to all the storage 

so do not know if that had anything to do with it

to note while I do have UEFI mobo I did not install either OS in UEFI mode just to be sure they work well together

if anyone can tell what is going on here

---

### Post by oldfred on 2014-03-25
Post these:
sudo parted -l
 sudo gdisk -l /dev/sdb

If you do not have gdisk
sudo apt-get install gdisk

Did you use Windows to create the gpt partitions or Linux tools like gdisk or gparted?

---

### Post by dodoking on 2014-03-25
yes i used windows and like I said the grub menu disappeared this was even before I created the partition 

as soon as I attached the HDD and booted back on no grub menu loaded straight to windows 7.
 I will try to use a live version to post what you ask

---

### Post by dodoking on 2014-03-25
gdisk info

**sudo parted -l**

Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs


Model: ATA ST4000VN000-1H41 (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   4001GB  4001GB  ntfs         Basic data partition          msftdata


Model: ATA WDC WD6402AAEX-0 (scsi)
Disk /dev/sdc: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   533GB  533GB   primary   ntfs
 3      533GB   640GB  107GB   extended
 5      533GB   632GB  98.8GB  logical   ext4
 6      632GB   640GB  8548MB  logical   linux-swap(v1)


Model: Intenso Rainbow (scsi)
Disk /dev/sdd: 15.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1237kB  15.9GB  15.9GB  primary  fat32        boot, lba

**sudo gdisk -l /dev/sdb**

GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 7814037168 sectors, 3.6 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): FAC8FB08-8EDF-4E1C-9129-35062ECB2E3A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 8-sector boundaries
Total free space is 3693 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192      7814035455   3.6 TiB     0700  Basic data partition

---

### Post by oldfred on 2014-03-26
All that looks normal.

Is issue just which drive is set as default boot in BIOS?
Grub always installs to sda when you use any of the auto install options, but which drive is sda may not be the drive you install Ubuntu into. Best to have grub installed to the MBR of the same drive as Ubuntu.

Try booting from all other drives.

If you cannot boot run this, but do not run auto repair as that will install grub to all drives.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

