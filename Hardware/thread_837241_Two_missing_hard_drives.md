---
title: "Two missing hard drives"
date: 2008-06-22
forum: Hardware
---

### Post by Frogster on 2008-06-22
Scratching my head on this one. I have four hard drives but 7.10 only sees two! The two invisibles have windows data on them so I would like to be able to access them.

Any pointers or help would be very much appreciated. GParted sees the drives but reports them as unallocated and  lshw -C disk reports

keith@Ernie:~$ sudo lshw -C disk
[sudo] password for keith:
  *-disk:0                
       description: SCSI Disk
       product: ST3160812AS
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5LSBYB49
       size: 149GB
       configuration: ansiversion=5
  *-disk:1
       description: SCSI Disk
       product: ST3160811AS
       vendor: ATA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 6PT10J41
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:0
       description: ATA Disk
       product: Maxtor 6E040L0
       vendor: Maxtor
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: NAR61EA0
       serial: E1069Y7N
       size: 38GB
       capacity: 38GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma6 smart=on
  *-disk:1
       description: ATA Disk
       product: Maxtor 6Y080L0
       vendor: Maxtor
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: YAR41BW0
       serial: Y26WY0MC
       size: 76GB
       capacity: 76GB
       capabilities: ata dma lba iordy smart security pm apm
       configuration: apm=off mode=udma6 smart=on

---

### Post by Odrodzona-Sarmacja on 2008-06-22
"sudo blkid" should give you listing of all devices detected by your Ubuntu.

---

### Post by Frogster on 2008-06-23
Thank you for the reply. 

Ubuntu seems only to see:

keith@Ernie:~$ sudo blkid
[sudo] password for keith:
/dev/hda1: UUID="7AE820ADE8206A19" LABEL="Martha" TYPE="ntfs" 
/dev/sdb1: UUID="5eaab39e-5794-47f2-ba11-2fcc140fa582" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="11e57445-5f48-4a46-96e0-15148af2acf0" 
/dev/sda: UUID="624842624841AB7" TYPE="ntfs" 

How do I get the other disks to show up, do I just mount the disks and if so will that keep the data that is on them?

---

### Post by sisco311 on 2008-06-23
post the output from:
```
sudo fdisk -l
```
and
```
mount
```

---

### Post by Frogster on 2008-06-23
Here you go.....

keith@Ernie:~$ sudo fdisk -l
[sudo] password for keith:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x180b180a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x9ad2d170

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a6431cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18700   150207718+  83  Linux
/dev/sdb2           18701       19457     6080602+   5  Extended
/dev/sdb5           18701       19457     6080571   82  Linux swap / Solaris

and 

keith@Ernie:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda on /media/Smithy type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hda1 on /media/Martha type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

---

### Post by Odrodzona-Sarmacja on 2008-06-23
```

keith@Ernie:~$ sudo blkid
[sudo] password for keith:
/dev/hda1: UUID="7AE820ADE8206A19" LABEL="Martha" TYPE="ntfs" 
/dev/sdb1: UUID="5eaab39e-5794-47f2-ba11-2fcc140fa582" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="11e57445-5f48-4a46-96e0-15148af2acf0" 
/dev/sda: UUID="624842624841AB7" TYPE="ntfs" 

```

I see three hard drives detected. Two windows ntfs and one linux ext3. If there are some hard drives attached like a fourth hard drive, then I would go checking their jumpers and cable connections again. If everything sticks together on hardware level as should be and I still don't get "sudo blkid" to show them, then I think I would go to BIOS and turn off automation for plug&play oses, so BIOS settings are set for non-plug&play os and have then the BIOS reconfigure itself its hardware setup. If BIOS detects all four hard drives and it is set to non plug&play, then no os should have problems with detecting this hardware setup. At least that's what I would do in situation like this. I don't know if it will help anyhow.

---

### Post by Frogster on 2008-06-23
Thank you Odrodzona-Sarmacja. I will check the cables as you suggest and prod the bios.

---

### Post by Frogster on 2008-07-01
*Shakes Head* it seems that unplugging the drives and reregistering the drives in the bios has made no difference at all.

---

