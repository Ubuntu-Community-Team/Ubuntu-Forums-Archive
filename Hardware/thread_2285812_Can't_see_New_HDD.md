---
title: "Can't see New HDD"
date: 2015-07-08
forum: Hardware
---

### Post by Rick St. George on 2015-07-08
System: 8 Core AMD CPU; 250 SSD; 16GB Ram; Ubuntu Studio v14.04

Just installed a 1TB ST SATA HDD and doesn't mount or show up in File Mgr. I thought well maybe I need to Format it, as it is a Recertified drive. Figured I should use gparted to create a partition table & format the drive, but is that command in Ubuntu, or should I pop a CD with it on their and boot from it?

It does show up using FDISK - see below.

Here is a partial printout that I believe shows the relevant info;

```

[    1.407211] scsi0 : pata_atiixp
[    1.408090] scsi1 : pata_atiixp
[    1.408216] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.408219] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.408301] ahci 0000:00:11.0: version 3.0
[    1.408499] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.408503] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.409163] scsi2 : ahci
[    1.409270] scsi3 : ahci
[    1.409359] scsi4 : ahci
[    1.409478] scsi5 : ahci
[    1.409558] ata3: SATA max UDMA/133 abar m1024@0xfe30b000 port 0xfe30b100 irq 19
[    1.409561] ata4: SATA max UDMA/133 abar m1024@0xfe30b000 port 0xfe30b180 irq 19
[    1.409563] ata5: SATA max UDMA/133 abar m1024@0xfe30b000 port 0xfe30b200 irq 19
[    1.409566] ata6: SATA max UDMA/133 abar m1024@0xfe30b000 port 0xfe30b280 irq 19
[    1.576939] ata1.00: supports DRM functions and may not be fully accessible
[    1.576942] ata1.00: ATA-9: Samsung SSD 840 EVO 250GB, EXT0BB6Q, max UDMA/133
[    1.576944] ata1.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    1.576949] ata1.01: ATAPI: HL-DT-ST DVDRAM GH24NSB0, LN01, max UDMA/133
[    1.576952] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.576953] ata1.01: limited to UDMA/33 due to 40-wire cable
[    1.580034] ata1.00: supports DRM functions and may not be fully accessible
[    1.580038] ata1.00: configured for UDMA/33
[    1.585846] ata1.01: configured for UDMA/33
[    1.588880] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 840  EXT0 PQ: 0 ANSI: 5
[    1.589046] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.589056] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.594877] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GH24NSB0  LN01 PQ: 0 ANSI: 5
[    1.594935] sd 0:0:0:0: [sda] Write Protect is off
[    1.594938] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.599097] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.604363] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.604366] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.604492] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.604572] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.608242]  sda: sda1 sda2 < sda5 >
[    1.608686] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.714800] ata4: SATA link down (SStatus 0 SControl 300)
[    1.714835] ata3: SATA link down (SStatus 0 SControl 300)
[    1.870043] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.870077] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.871411] ata6.00: ATA-8: ST31000524AS, JC4B, max UDMA/133
[    1.871414] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.871449] ata5.00: ATA-8: WDC WD2500BEVT-22A23T0, 01.01A01, max UDMA/133
[    1.871452] ata5.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.872930] ata5.00: configured for UDMA/133
[    1.872942] ata6.00: configured for UDMA/133
[    1.873033] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.873182] sd 4:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.873184] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    1.873329] sd 4:0:0:0: [sdb] Write Protect is off
[    1.873331] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.873354] scsi 5:0:0:0: Direct-Access     ATA      ST31000524AS     JC4B PQ: 0 ANSI: 5
[    1.873371] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.873488] sd 5:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.873499] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    1.873591] sd 5:0:0:0: [sdc] Write Protect is off
[    1.873593] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.873631] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.876702]  sdc: unknown partition table
[    1.877036] sd 5:0:0:0: [sdc] Attached SCSI disk
[    1.914500]  sdb: sdb1
[    1.914912] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.019064] random: nonblocking pool is initialized
[    2.058093] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)


```


AND THIS INFO

```

sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050abd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   454946815   227472384   83  Linux
/dev/sda2       454948862   488396799    16723969    5  Extended
/dev/sda5       454948864   488396799    16723968   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009d9ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

---------------------------------------------------------

sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  233GB  233GB   primary   ext4            boot
 2      233GB   250GB  17.1GB  extended
 5      233GB   250GB  17.1GB  logical   linux-swap(v1)


Model: ATA WDC WD2500BEVT-2 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  250GB  250GB  primary  ntfs


Error: /dev/sdc: unrecognised disk label     


```

It shows above - "unrecognized disk label" and "no valid partition table". 
It shows up as Device SDC, but how do I access it and Format it, so Ubuntu can Read/Write to it.
And can I use the entire 1TB or should I break it up for Ubuntu?

Thanks,
Rick

---

### Post by dino99 on 2015-07-08
you get  ****Disk /dev/sdc doesn't contain a valid partition table******

so fix that issue first

you may use gparted live cd/usb to prepare the device; but first be sure it is found / well identified by the bios/uefi

---

### Post by Rick St. George on 2015-07-08
Yes - it is found by the BIOS, but is Gparted not in Ubuntu? In other words, can I use it in Terminal? 

Thanks

---

### Post by Dennis N on 2015-07-08
> **Rick St. George said:**
> Yes - it is found by the BIOS, but is Gparted not in Ubuntu? In other words, can I use it in Terminal? 

Thanks

If you have ubuntu on the 250 gB, you can work on the other disk from there. gparted is available in the repositories if it is not already installed on your system. It should find your disk if it is connected and allow you to work on it from it's gui.

---

### Post by Rick St. George on 2015-07-08
Ran gparted in Terminal with sudo command, made 2 partitions to break up the 1 TB drive into 2 500 GB partitions as EXT4.
But now can't write to it. Paste is greyed out! Did I miss something ???

This is what I get now ...

[CODE]

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  ee  GPT

[/CODE}

Thanks

---

### Post by Dennis N on 2015-07-08
> **Rick St. George said:**
> Ran gparted in Terminal with sudo command, made 2 partitions to break up the 1 TB drive into 2 500 GB partitions as EXT4.
But now can't write to it. Paste is greyed out! Did I miss something ???

Thanks
Newly created partitions are owned by root, so you can't write to them until you change the ownership of the filesystem on each partiton.

---

### Post by Rick St. George on 2015-07-08
In gparted, partition types are - aix; amiga; bsd; dvh; gpt; mac; msdos; pc98; sun; loop.

Which one for use strictly with my Ubuntu Studio installation? And how do I change Ownership (will look it up) ?

thanks!

---

### Post by Dennis N on 2015-07-08
Those are types of partition _tables_. EXT4 is the partition type. It's for Linux.

---

### Post by Rick St. George on 2015-07-08
Followed instructions in your Link above. Ran these commands, still can't Write to Disk

```

  *-disk
       description: ATA Disk
       product: ST31000524AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: JC4B
       serial: 5VP55JPG
       size: 931GiB (1TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=ac105d89-2dd5-491d-95bf-a1d917539d8f sectorsize=512
stephen@stephen-evo-5723:~$ sudo mkdir /media/seagate1
stephen@stephen-evo-5723:~$ gksu gedit /etc/fstab.d
stephen@stephen-evo-5723:~$ sudo chown -R stephen:stephen /media/seagate1
stephen@stephen-evo-5723:~$ sudo mount /dev/sdc1 /media/seagate1
stephen@stephen-evo-5723:~$ sudo mount /dev/sdc2 /media/seagate1
stephen@stephen-evo-5723:~$ sudo mount -a
stephen@stephen-evo-5723:~$ sudo chown -R stephen:stephen-evo-5723 /media/seagate1
chown: invalid group: &#8216;stephen:stephen-evo-5723&#8217;
stephen@stephen-evo-5723:~$ sudo chown -R 1000 /media/seagate1


```

Note: There is no FSTAB file in / etc. There is a fstab.d  which is a directory. When I go to File Mgr / media / seagate1, I see a folder "lost+found".
Do the two partitions not supposed to show?
Still can't write to partition ST01. Any suggestions - thanks!

---

### Post by Rick St. George on 2015-07-08
I am doing something Wrong???  STO2 now shows up (when Righ Click in dir) as owner stephen with R/W; group stephen with Read Only permissions.

ST01 shows up as Root with R/W; group root with Read Only.

In Gparted; it shows ST01 is mounted in media/seagate1; STO2 does not show as mounted.  

Ran these commands;

```

stephen@stephen-evo-5723:~$ sudo mount /dev/sdc2 /media/seagate1/ST02
mount: mount point /media/seagate1/ST02 does not exist
stephen@stephen-evo-5723:~$ sudo mkdir /media/seagate1/STO2
stephen@stephen-evo-5723:~$ sudo mount /dev/sdc2 /media/seagate1/ST02
mount: mount point /media/seagate1/ST02 does not exist
stephen@stephen-evo-5723:~$ sudo chown stephen: /media/seagate1/ST02
chown: cannot access &#8216;/media/seagate1/ST02&#8217;: No such file or directory
stephen@stephen-evo-5723:~$ sudo chown stephen: /media/seagate1/ST02
chown: cannot access &#8216;/media/seagate1/ST02&#8217;: No such file or directory
stephen@stephen-evo-5723:~$ sudo chown stephen: /media/seagate1/ST01
chown: cannot access &#8216;/media/seagate1/ST01&#8217;: No such file or directory
stephen@stephen-evo-5723:~$ sudo chown stephen: /media/seagate1
stephen@stephen-evo-5723:~$ 


```

What gives ? ? ?  I'm stumped ! ! !

---

### Post by Rick St. George on 2015-07-08
Will Mark .... SOLVED:

After looking again in File Mgr., noticed it is actually mounted under username.
After ReBooting, saw the two partitions mounted at ... media/username/ST01 and media/username/ST02.

Now copying files to that drive. 
Thanks for all the help!

Rick

---

