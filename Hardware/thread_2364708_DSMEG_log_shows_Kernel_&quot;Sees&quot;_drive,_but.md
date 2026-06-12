---
title: "DSMEG log shows Kernel &quot;Sees&quot; drive, but nothing else can &quot;See&quot; it."
date: 2017-06-26
forum: Hardware
---

### Post by whereismymindat2 on 2017-06-26
Running Xubuntu 16.04.2

Question. I have TWO Internal WDC ("WD Blue") 1TB 6.0_GBS transfer. 
WD Blue 1TB SATA 6 Gb/s 7200 RPM 64MB Cache 3.5 Inch Desktop Hard Drive (WD10EZEX)
(more specs if needed): [https://www.amazon.com/Blue-Cache-Desktop-Drive-WD10EZEX/dp/B0088PUEPK](https://www.amazon.com/Blue-Cache-Desktop-Drive-WD10EZEX/dp/B0088PUEPK)

I've tried to use Everything to "Recover"that drive, nothing works (AKA testdisk,others). To even "SEE" it. 

Could this be "why". Noticed in the Logs my "Primary Drive" loads as expected but using "ata" 
The *NOT* "seen"/mountable" some reason shows it's a scsi drive (not the "ata" above). 

My Architecture amd64 
x86_64. 
I enabled my CPU to be able to see 32-bit applications / able to install-on box. 

Drive 2-"Unseen" drive. 
Is a drive (previously used as a "Storage Drive") on a former 32-bit box. Could this be a problem? 


Copy of Chopped dmesg Logs. 

```


root@Dawg:~# dmesg  | grep ATA
[    1.142504] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.143641] ata3.00: ATA-10: WDC WD10EZEX-08xxxx, 01.01A01, max UDMA/100

.......................................
THIS WORKS AS DESIRED.
...............................
[    1.142504] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.143121] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.143123] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.143124] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.143641] ata3.00: ATA-10: WDC WD10EZEX-08xxxx, 01.01A01, max UDMA/100
[    1.143642] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.144276] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.144278] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.144279] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.144345] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.144347] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.144349] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.144876] ata3.00: configured for UDMA/100


MY 2nd Internal Drive has only *ONE* line in the DMSEG LOG. 

[    1.180753] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EZEX-08y yyyy PQ: 0 ANSI: 5

```

Thanks in advance for the help. !

---

### Post by efflandt on 2017-06-27
Whether your OS is 32-bit or 64-bit should have nothing to do with drive access. I have a PC from 2004 with the first Athlon64 3200+ (2.0 GHz) that came with 32-bit WinXP. At some point I freed up some space to install 64-bit WinXP Pro beta and 64-bit SuSE (8.2 maybe), eventually the 64-bit WinXP beta expired, and SuSE was old, so I replaced those with separate 32 and 64-bit installations of Ubuntu 10.04. I guess I should upgrade that one of these days (the PC works with 64-bit 16.04 live/install booted from USB stick).

The lack of details in dmesg for that drive might mean some sort of major drive failure, possibly electronic, since it does not even get as far as checking spec's. Although, for **ata2.00** (which I assume is that drive) it does say **(SET FEATURES) succeeded**. Normally somewhere following the scsi line is an sd line for storage drives (sg for optical drives).```
~$ dmesg | grep scsi
[    1.192907] scsi host0: ahci
[    1.193206] scsi host1: ahci
[    1.193428] scsi host2: ahci
[    1.193559] scsi host3: ahci
[    1.193631] scsi host4: ahci
[    1.193711] scsi host5: ahci
[    1.523254] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1002FAEX-0 1D05 PQ: 0 ANSI: 5
[    1.552183] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.894481] scsi 1:0:0:0: Direct-Access     ATA      Crucial_CT512M55 MU01 PQ: 0 ANSI: 5
[    1.927866] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.933080] scsi host6: usb-storage 2-1.2:1.0
[    2.262515] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GH50N    B103 PQ: 0 ANSI: 5
[    2.292483] sr 2:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.292830] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.292893] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    2.945049] scsi 6:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    2.945794] scsi 6:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.946467] scsi 6:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    2.947021] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0
[    2.947464] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    2.947687] sd 6:0:0:1: Attached scsi generic sg4 type 0
[    2.947820] sd 6:0:0:2: Attached scsi generic sg5 type 0
[    2.947970] sd 6:0:0:3: Attached scsi generic sg6 type 0
```And ata lines should show more about the drive.```
~$ dmesg | grep ata
--snip --
[    1.508668] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.520465] ata1.00: ATA-8: WDC WD1002FAEX-00Z3A0, 05.01D05, max UDMA/133
[    1.520468] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.522829] ata1.00: configured for UDMA/133
[    1.868656] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.869018] ata2.00: supports DRM functions and may not be fully accessible
[    1.876929] ata2.00: disabling queued TRIM support
[    1.876932] ata2.00: ATA-9: Crucial_CT512M550SSD3, MU01, max UDMA/133
[    1.876935] ata2.00: 1000215216 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.881694] ata2.00: supports DRM functions and may not be fully accessible
[    1.889606] ata2.00: disabling queued TRIM support
[    1.893987] ata2.00: configured for UDMA/133
[    1.927837] ata2.00: Enabling discard_zeroes_data
[    1.928028] ata2.00: Enabling discard_zeroes_data
[    1.928364] ata2.00: Enabling discard_zeroes_data
[    2.244177] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.247217] ata3.00: ATAPI: HL-DT-ST DVD+/-RW GH50N, B103, max UDMA/100
[    2.250977] ata3.00: configured for UDMA/100
[    2.608425] ata4: SATA link down (SStatus 0 SControl 300)
[    2.920695] ata6: SATA link down (SStatus 0 SControl 300)
[    7.353949] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    7.477193] systemd[1]: Set hostname to <msata512-1610>.
[   81.793163] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[101262.015413] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
```Note that I am running from mSATA (sdb1) in SATA adapter and partition(s) on my WDC drive (sda) only mount when I access something on that drive with File Manager (nautilus). I have a cron.hourly script that puts the WDC drive in standby if not mounted and not active, to run silently with slightly less idle power most of the time.

Does anything show for that drive doing either of these commands:```
sudo fdisk -l
sudo parted -l
```

---

### Post by whereismymindat2 on 2017-06-30
1st--That's another "Bizarre" occurrence...It's changing (jumping around) daily what results I get via

sudo fdisk -l
sudo parted -l

Example, I also have "failed" USB drives Attached (they all "shot"/"broke" at same time).
However, drives will occasionally show up (one did, and allowed it mountable,etc.) until I did a reboot and *POOF* back to "BAD" state.

Examples.
Today June 30th
sudo fdisk -l
```


banter@Dawg:~$ sudo fdisk -l

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1        2047 1953523711 1953521665 931.5G  f W95 Ext'd (LBA)
/dev/sda5        2048 1953523711 1953521664 931.5G 83 Linux

Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 05A05D70-2730-0A46-B531-7D9ADCDB522B

Device          Start        End   Sectors   Size Type
/dev/sdb1        2048   19531344  19529297   9.3G Linux filesystem
/dev/sdb2    19531776   39063551  19531776   9.3G Linux filesystem
/dev/sdb3    39063552   97656831  58593280    28G Linux filesystem
/dev/sdb4   210937856  230469105  19531250   9.3G Linux filesystem
/dev/sdb5  1910157312 1929689087  19531776   9.3G Linux swap
/dev/sdb6   367187968  855470079 488282112 232.9G Linux filesystem
/dev/sdb7   855470080  933595135  78125056  37.3G Linux filesystem
/dev/sdb8   933595136 1519532031 585936896 279.4G Linux filesystem
/dev/sdb9  1519532032 1910157311 390625280 186.3G Linux filesystem
/dev/sdb11   97656832  195313663  97656832  46.6G Linux filesystem
/dev/sdb12  230469632  269531135  39061504  18.6G Linux filesystem

Partition table entries are not in disk order.




Disk /dev/sde: 30 GiB, 32176472064 bytes, 62844672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000696d3

Device     Boot Start      End  Sectors Size Id Type
/dev/sde1  *     2048 62842879 62840832  30G  b W95 FAT32


Disk /dev/sdd: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: 0A7DFD1A-11D5-4C37-9BC8-6B1750138E89

```

Naturally my "Boot Disk" supposed to be on /dev/sda, but now showing up on /dev/sdb

Today June 30th
sudo parted -l



```

banter@Dawg:~$ sudo parted -l
[sudo] password for banter:
Model: LaCie P9220 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number Start End Size Type File system Flags
1 1048kB 1000GB 1000GB extended lba
5 1049kB 1000GB 1000GB logical


Model: ATA WDC WD10EZEX-08W (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number Start End Size File system Name Flags
1 1049kB 10.0GB 9999MB ext4
2 10.0GB 20.0GB 10.0GB ext4
3 20.0GB 50.0GB 30.0GB ext4
11 50.0GB 100GB 50.0GB ext4
4 108GB 118GB 10.0GB ext4
12 118GB 138GB 20.0GB ext4
6 188GB 438GB 250GB ext4
7 438GB 478GB 40.0GB ext4
8 478GB 778GB 300GB ext4
9 778GB 978GB 200GB ext4
5 978GB 988GB 10.0GB linux-swap(v1)


Model: LaCie P9220 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number Start End Size File system Name Flags


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sde: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number Start End Size Type File system Flags
1 1049kB 32.2GB 32.2GB primary fat32 boo


```


fyi--the Model: PNY USB 2.0 FD (scsi)-is a USB stick, created to put "Multisystem" on. I'm putting Rescue Disk Material to boot into that. Thus I assume the "necessity" for a boot flag(???)

........................................


6-28-2017 
fdisk -l


```

banter@Dawg:~$ sudo fdisk -l
[sudo] password for banter: 
Sorry, try again.
[sudo] password for banter: 
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 05A05D70-2730-0A46-B531-7D9ADCDB522B

Device          Start        End   Sectors   Size Type
/dev/sda1        2048   19531344  19529297   9.3G Linux filesystem
/dev/sda2    19531776   39063551  19531776   9.3G Linux filesystem
/dev/sda3    39063552   97656831  58593280    28G Linux filesystem
/dev/sda4   210937856  230469105  19531250   9.3G Linux filesystem
/dev/sda5  1910157312 1929689087  19531776   9.3G Linux swap
/dev/sda6   367187968  855470079 488282112 232.9G Linux filesystem
/dev/sda7   855470080  933595135  78125056  37.3G Linux filesystem
/dev/sda8   933595136 1519532031 585936896 279.4G Linux filesystem
/dev/sda9  1519532032 1910157311 390625280 186.3G Linux filesystem
/dev/sda11   97656832  195313663  97656832  46.6G Linux filesystem
/dev/sda12  230469632  269531135  39061504  18.6G Linux filesystem

Partition table entries are not in disk order.



Disk /dev/sdg: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0x59004129

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdg1  *     2048 1953523711 1953521664 931.5G 83 Linux


Disk /dev/sdh: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: B4F9926F-4F4E-42F6-81AD-D5DA48B493DE


Disk /dev/sdj: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: 7DD9D95F-4D94-419D-B2F8-76706A6F2FB9


```


then...... 
6-28-2017 
parted -l


```

root@Dawg:~# parted -l
Model: ATA WDC WD10EZEX-08W (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  10.0GB  9999MB  ext4
 2      10.0GB  20.0GB  10.0GB  ext4
 3      20.0GB  50.0GB  30.0GB  ext4
11      50.0GB  100GB   50.0GB  ext4
 4      108GB   118GB   10.0GB  ext4
12      118GB   138GB   20.0GB  ext4
 6      188GB   438GB   250GB   ext4
 7      438GB   478GB   40.0GB  ext4
 8      478GB   778GB   300GB   ext4
 9      778GB   978GB   200GB   ext4
 5      978GB   988GB   10.0GB  linux-swap(v1)


Model: ST2000DL 003-9VT166 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdc: 32.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End  Size  Type  File system  Flags


Warning: Unable to open /dev/sdd read-write (Read-only file system).  /dev/sdd
has been opened read-only.
Model: PNY USB 2.0 FD (scsi)                                              
Disk /dev/sdd: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  32.2GB  32.2GB  primary


Error: /dev/sdi: unrecognised disk label
Warning: Error fsyncing/closing /dev/sdi: Input/output error
Retry/Ignore? R                                                           
Warning: Error fsyncing/closing /dev/sdi: Input/output error
Retry/Ignore? I                                                           
Model: LaCie P9220 (scsi)
Disk /dev/sdi: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

Model: LaCie P9220 (scsi)
Disk /dev/sdg: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               boot


Model: LaCie P9220 (scsi)
Disk /dev/sdj: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags


Model: LaCie P9220 (scsi)
Disk /dev/sdh: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags



```


Thus example, "today" the 3-Lacie USB Drives attached are not being "SEEN" (but were seen on the 6-28-2017 results. 

*AND* as I'm typing this a USB Lacie is appearing/disappearing on my desktop (but is unmountable).

---

