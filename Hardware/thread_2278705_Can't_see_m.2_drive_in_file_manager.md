---
title: "Can't see m.2 drive in file manager"
date: 2015-05-18
forum: Hardware
---

### Post by dangillmor on 2015-05-18
Running 14.04.2, 4.0 kernel, on ThinkPad T450s, and can't see the m.2 Windows drive.  It's definitely there (sdb2 according to fdisk -l; see below). Not sure how to make it visible in Nautilus.


When I run Disks the drive shows up as sdb and a partition as sdb1, but partition type is "unknown" --


Ideas?


$ sudo fdisk -l


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4300


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
/dev/sda5          501760  1953523711   976510976   83  Linux


Disk /dev/sdb: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bd54a7d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     3071999     1534976    7  HPFS/NTFS/exFAT
/dev/sdb2         3072000   467980287   232454144    7  HPFS/NTFS/exFAT
/dev/sdb3       467980288   500115455    16067584    7  HPFS/NTFS/exFAT


Disk /dev/sdb1: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bd54a7d


     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *        2048     3071999     1534976    7  HPFS/NTFS/exFAT
/dev/sdb1p2         3072000   467980287   232454144    7  HPFS/NTFS/exFAT
/dev/sdb1p3       467980288   500115455    16067584    7  HPFS/NTFS/exFAT

---

### Post by Vladlenin5000 on 2015-05-18
You cannot mount hibernated partitions, the default behaviour in Windows 8.x. Your best chance is to disable fasboot (in Windows) and then shutdown (not reboot) before running Ubuntu. This may not work either. It all depends on how the Windows is installed.

Note: As a general rule you shouldn't mount/write to the Windows system partitions. Mounting and using a NTFS _data_ should be fine.

---

### Post by dangillmor on 2015-05-18
It's Windows 7 and I'm pretty sure I'm just shutting it down, not hibernating...

---

### Post by oldfred on 2015-05-18
Partitions have a partition boot sector (PBR) that is just like the MBR or space for boot code which Windows normally uses and space for a partition table, which is normally only used by  logical partition to have an entry to chain to the next entry.

Post this, just to see if you have same results:
sudo parted -l

But your sdb1 partition seems to be identical to the sdb MBR. Same entries, same sizes?

Did you run a dd command or something else that copied MBR to PBR?

How Windows boots MBR and PBR:
 [http://www.multibooters.co.uk/mu]("http://www.multibooters.co.uk/multiboot.html")

---

### Post by dangillmor on 2015-05-23
No, I didn't do a dd on this. Output as requested:

$ sudo parted -l
[sudo] password for dan: 
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical




Model: ATA TS256GMTS400 (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1573MB  1572MB  primary  ntfs         boot
 2      1573MB  240GB   238GB   primary  ntfs
 3      240GB   256GB   16.5GB  primary  ntfs




Model: Seagate BUP Slim SL (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size   Type     File system  Flags
 1      32.3kB  510GB   510GB  primary
 2      510GB   1010GB  500GB  primary
 3      1010GB  1500GB  490GB  primary  ntfs




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 12.6GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  12.6GB  12.6GB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 987GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  987GB  987GB  ext4




Error: /dev/mapper/sda5_crypt: unrecognised disk label

---

### Post by dangillmor on 2015-05-23
I ran chkdsk and shut down completely, with same result. Definitely not hibernated...

---

### Post by oldfred on 2015-05-23
Did you run chkdsk on all three NTFS partitions?
I just have not seen a partition table entry like your sdb2, it may be valid, but is unusual.

Run this just as it includes more info on MBR & PBR which is otherwise difficult to extract.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by dangillmor on 2015-05-25
Here's the boot-info report:

[http://paste.ubuntu.com/11356345/](http://paste.ubuntu.com/11356345/)

---

### Post by oldfred on 2015-05-25
Fhe only issues seem to be related to the standard tools Boot-Repair uses that do not work with LVM or encrypted partitions, so those seem to be normal.

Not sure what else to suggest.

You can just add your own boot stanza to 40_custom. But Windows really likes to be sda, did you move it from sda to sdb?  And if not seen as NTFS it still may not work.

```
 menuentry "Microsoft Windows Vista/7/8 BIOS-MBR" {
    insmod part_msdos
    insmod ntfs
    insmod search_fs_uuid
    insmod ntldr     
    search --fs-uuid --no-floppy --set=root --hint-bios=hd1,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 69B235F6749E84CE
    ntldr /bootmgr
}



```

---

### Post by dangillmor on 2015-05-28
Not at all sure why it's sdb, actually...I'll try adding your code and see what happens.

---

### Post by oldfred on 2015-05-28
Just noticed, I posted standard entry for Windows in sda1. Since bios hint is changed to hd1 it may work but you may also need to change the others also.

hint-bios=hd1,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1

---

