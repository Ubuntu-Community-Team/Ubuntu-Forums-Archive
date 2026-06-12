---
title: "NTFS/FAT RAID - So close, and yet ..."
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by neurosion on 2005-05-29
Ubuntu closed the deal for me; I'm now determined to do most of my work on Linux.

Unfortunately, there are some things (like my job) that I have to keep my WinXP SP2 partition around for.  The only information I really need on both operating systems, though, is my music, so I'm trying to set that up on a separate partition (with Partition Magic 8.0).

I followed these instructions: [http://www.ubuntuforums.org/showthread.php?t=2557](http://www.ubuntuforums.org/showthread.php?t=2557) to gain access to the striped SATA RAID on the VIA 6420 controller of my Asus A8V.  Unfortunately, I can't mount the partitions.  They're in /dev/mapper/:

```
neurosion@neurosion-amd64:/ # ls /dev/mapper/
control  via_ddebgfbehh  via_ddebgfbehh1  via_ddebgfbehh5
```
fdisk sees everything fine:

```
Disk /dev/mapper/via_ddebgfbehh: 320.0 GB, 320083770368 bytes
255 heads, 63 sectors/track, 38914 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                     Device Boot      Start         End      Blocks   Id  System
/dev/mapper/via_ddebgfbehh1   *           1       31265   251136081    7  HPFS/N TFS
/dev/mapper/via_ddebgfbehh2           31266       38914    61440592+   f  W95 Ex t'd (LBA)
/dev/mapper/via_ddebgfbehh5           31266       38914    61440561    7  HPFS/N TFS
```
But when I try to mount the partition (via_ddebgfbehh5 is the partition of interest), I have no success:

```
neurosion@neurosion-amd64:/ # mount /dev/mapper/via_ddebgfbehh5 /mnt/share/ -t ntfs -o umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/mapper/via_ddebgfbehh5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

neurosion@neurosion-amd64:/ # dmesg | grep ntfs
NTFS-fs error (device dm-4): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device dm-4): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device dm-4): ntfs_fill_super(): Not an NTFS volume.
```

I've tried switching to a FAT32 partition and that didn't work either.  I even tried mkfs.vfat, which actually made the partition mountable, but then the partition was completely bogus from WinXP's point of view.

I've been working on this for several hours, using every resource Google can offer, but ultimately I'm stumped.  Any help the community could offer would be appreciated.

---

### Post by neurosion on 2005-05-29
Pardon the single bump, but I've seen people claiming success with this situation and I'm hoping one of them will notice.

---

