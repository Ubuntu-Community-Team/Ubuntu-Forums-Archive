---
title: "external esata drive not detected - windows sees drive ubuntu does not"
date: 2014-12-15
forum: Hardware
---

### Post by DJonsson2008 on 2014-12-15
Product Name: HP EliteBook 8440w
Chipset : Intel QM57 
OS: Ubuntu/Xubuntu 14 LTS

After attempting everything I could find in the forums I'm still unable to see an external Esata drive in Ubuntu 14.

The same drive connects instantly in Windows 7 so I know there is no hardware issue, but can't get Ubuntu or Xubuntu os to see the drive.

I'm not trying to boot from the drive but simply work on files on the drive, for this Ubuntu does not recognize or see the drive at all.

While the output shows 2 Intel drives the drive I'm attempting to connect is -- **a 3rd drive which Ubuntu does not see.**

Per recomendations in these forums I've run the following command line tools and commands.

**sudo fdisk -l** -- does not recognize the esata drive.
**sudo blkid** -- does not recognize the esata drive or any of its partitions.
**sudo scsitools rescan-scsi-bus** - does not see the esata drive 

I'm unable to tell what dmesg is telling me, other than seeing different response on ata5 when the drive after the drive is detatched.
I'm not sure in fact if ata5 is referencing the esata drive, so that may be false lead.

Any comments or links to solutions appreciated.

Notes follow


********************************************************************************
~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x744d8e47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      131071       64512    7  HPFS/NTFS/exFAT
/dev/sda2          131072   207890431   103879680    7  HPFS/NTFS/exFAT
/dev/sda3       208381952   233326591    12472320    7  HPFS/NTFS/exFAT
/dev/sda4       233326592   234440703      557056    c  W95 FAT32 (LBA)

Disk /dev/sdb: 40.0 GB, 40019582464 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78163247 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00045b88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    61681663    30839808   83  Linux
/dev/sdb2        61683710    78161919     8239105    5  Extended
/dev/sdb5        61683712    78161919     8239104   82  Linux swap / Solaris


********************************************************************************
>$ blkid

/dev/sda1: LABEL="SYSTEM" UUID="FA6441B164417205" TYPE="ntfs" 
/dev/sda2: UUID="922E612D2E610C13" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="2CB656DBB656A55C" TYPE="ntfs" 
/dev/sda4: LABEL="HP_TOOLS" UUID="8447-F1CD" TYPE="vfat" 
/dev/sdb1: UUID="3eb6f113-b1f1-4512-b00b-bda52c3e7a0c" TYPE="ext4" 
/dev/sdb5: UUID="66058b80-3b73-4bbd-84f6-83aba5cae25e" TYPE="swap" 


********************************************************************************
>$ dmesg

[    1.369287] ata5: SATA max UDMA/133 abar m2048@0xd7427000 port 0xd7427300 irq 44


[    2.594588] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.594693] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x100)

[    7.904955] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.905089] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[    7.905095] ata5: limiting SATA link speed to 1.5 Gbps
[   13.215284] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   13.215432] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   18.525636] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)


*********************************************************************************
* With ESATA drive nplugged dmesg has/adds these trailing lines.

[ 1121.830376] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 1121.830384] ata5: irq_stat 0x00400040, connection status changed
[ 1121.830388] ata5: SError: { PHYRdyChg 10B8B DevExch }
[ 1121.830396] ata5: hard resetting link
[ 1122.554226] ata5: SATA link down (SStatus 0 SControl 300)
[ 1122.554241] ata5: EH complete


~$ sudo rescan-scsi-bus
/sbin/rescan-scsi-bus: line 592: [: 1.13: integer expression expected
Host adapter 0 (ahci) found.
Host adapter 1 (ahci) found.
Host adapter 2 (ahci) found.
Host adapter 3 (ahci) found.
Host adapter 4 (ahci) found.
Host adapter 5 (ahci) found.
Host adapter 6 (pata_pcmcia) found.
Scanning SCSI subsystem for new devices
Scanning host 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 0 0 0 0 ... 
OLD: Host: scsi0 Channel: 00 Id: 00 Lun: 00
      Vendor: ATA      Model: INTEL SSDSC2MH12 Rev: PPG4
      Type:   Direct-Access                    ANSI SCSI revision: 05
Scanning host 1 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 1 0 0 0 ... 
OLD: Host: scsi1 Channel: 00 Id: 00 Lun: 00
      Vendor: ATA      Model: INTEL SSDSA2CT04 Rev: 4PC1
      Type:   Direct-Access                    ANSI SCSI revision: 05
Scanning host 2 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 3 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 4 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 5 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 6 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
0 new device(s) found.                     
0 device(s) removed.

---

### Post by houstonbofh on 2014-12-15
Your fdisk shows two drives connected.  If the 40GB is the esata drive you are recognized, but you may not be mounted.  Look in Computer to see if there are some drives to mount.

---

### Post by DJonsson2008 on 2014-12-15
> **houstonbofh said:**
> Your fdisk shows two drives connected.  If the 40GB is the esata drive you are recognized, but you may not be mounted.  Look in Computer to see if there are some drives to mount.

Thanks for your reply.

I should of mentioned in the original post 
the drive I'm attempting to connect is -- a 3rd drive which Ubuntu does not see.

1st of the drives appearing in fdisk is the Windows 7 OS, 
2nd drive is the Ubuntu OS drive.
the 3rd drive is an Intel 180 SSD fdisk does not see.

Per the connector I'm using the seagate GoFlex adapter which is reviewed and testing here as working with Linux.
[http://linuxandfriends.com/seagate-freeagent-goflex-ultra-portable-hard-drive-review/](http://linuxandfriends.com/seagate-freeagent-goflex-ultra-portable-hard-drive-review/)

Any suggestions appreciated.

---

