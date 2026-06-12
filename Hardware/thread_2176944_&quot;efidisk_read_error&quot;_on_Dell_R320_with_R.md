---
title: "&quot;efidisk read error&quot; on Dell R320 with RAID setup"
date: 2013-09-26
forum: Hardware
---

### Post by ep8HFdX on 2013-09-26
Hello.

I'm trying to install Ubuntu **12.04 LTS 64-bit** on a **Dell R320** server, which is setup with a RAID 1 (H310) for 2 SATA HDDs (for the OS and applications) and RAID 10 (H710) for 4 SAS HDDs (for data). 
I have setup the machine to boot with UEFI.

I burnt the ISO image of Ubuntu onto a CD and proceeded with the installation, choosing a guided installation with encrypted LVM.

After taking care of several options and seeing lots files getting copied, the system rebooted.

Once the initial boot information was displayed on screen, I got the following error: "efidisk read error". I thought the server had frozen there, but then Ubuntu was loaded normally (or so it seems).

Running ```
sudo parted /dev/sda print all
``` gives me the following:
> 
Model: DELL PERC H310 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End    Size   File system  Name  Flags
 1      17.4kB  200MB  200MB  fat32              boot
 2      200MB   456MB  256MB  ext2
 3      456MB   250GB  249GB                     lvm


Error: /dev/sdb: unrecognised disk label

Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 17.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  17.1GB  17.1GB  linux-swap(v1)


Error: /dev/mapper/te--server-swap_1: unrecognised disk label

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/te--server-root: 232GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  232GB  232GB  ext4


The RAID 10 volume is nowhere to be found.

Any suggestions?

Thank you in advance!

---

