---
title: "Cannot see all my harddrives"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by gezzabob on 2006-02-04
I have 5 hardrives plugged into my mobo (and 2 cdrom drives) but can only see 3 drives (and my 2 cdroms they are not a problem)

I have a gigabyte GA-7NNxp mobo

sata WD hdd 36GB - /dev/sda (connected via sata)



Matrox 120GB - /dev/hda

Seagate 160gb - /dev/hdb

a cdrom on /dev/hdc
the other cdrom on /dev/hdd

motherboard spec is

GA-7NNXP
nForce 2 Ultra400 chipset

Chipset
 - Super I/O: ITE IT8712F chip
 - Silicon Image sil3112A controller
 - GigaRAID ATA 133 RAID controller

Some other bit of info may be usefull

~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3               16G   1.2G    14G   8% /
tmpfs                  531M      0   531M   0% /dev/shm
tmpfs                  531M    13M   518M   3% /lib/modules/2.6.12-10-386/volatile
/dev/sda1               47M    16M    29M  36% /boot
/dev/sda5              9.9G   9.1G   284M  97% /home
/dev/hda5              123G   123G      0 100% /media/hda5
/dev/hdb1               33G    23G   9.3G  72% /fat_files
/dev/hdb2              123G    32G    86G  27% /media/hdb2
/dev/sda6              7.9G   3.4G   4.1G  46% /usr

~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/sda1 on /boot type ext2 (rw)
/dev/sda5 on /home type ext3 (rw)
/dev/hda5 on /media/hda5 type vfat (rw)
/dev/hdb1 on /fat_files type vfat (rw,iocharset=utf8,umask=000)
/dev/hdb2 on /media/hdb2 type ext3 (rw)
/dev/sda6 on /usr type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

$ sudo fdisk -l

Disk /dev/hda: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2      238216   120060360    f  W95 Ext'd (LBA)
/dev/hda5               2      238216   120060328+   b  W95 FAT32

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3902    31342783+   c  W95 FAT32 (LBA)
/dev/hdb2   *        3903       19079   121909252+  83  Linux
/dev/hdb3           19080       19457     3036285    5  Extended
/dev/hdb5           19080       19457     3036253+  82  Linux swap / Solaris

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  83  Linux
/dev/sda2               7         371     2931862+  82  Linux swap / Solaris
/dev/sda3             372        2316    15623212+  83  Linux
/dev/sda4            2317        4500    17542980    5  Extended
/dev/sda5            2317        3532     9767488+  83  Linux
/dev/sda6            3533        4500     7775428+  83  Linux

But I have 2 more hardddrives connected but cannot see them anywhere on the system.  A 120GB Maxtor and another harddrive I forget now what make and size.  It may be due to me having the wrong jumpers set on the drives or more than likley the 2 I cannot see are connected to the extra 2 IDE channels  on the motherboard and Ubuntu hasnt got the drivers install for them.  Any Ideas what programs / commands can I use to find the harddrive so I can mount them when I can find them I can then start working on a way to mount them etc thats not a problem its just finding them first :)

---

### Post by gezzabob on 2006-02-04
PS that /dev/sda6 could be my usb pen ? its not plugged in at the mo and every attempt I have tried to mount it as a harddrive has failed so I guess it is.

Sorry this is a bit of a mess but I have files here there and every where I am tring to clear them all up but need access to all my drives first before I can Begin

---

### Post by gezzabob on 2006-02-04
Sorry that sort of goes on question was ...

What programs or commands can I use to see all harddrive on my PC mounted or not.

I have tried hardinfo that doesnt show the 2 missing drives, qparted doesnt show them , and the other parted prog erm QTparted any other ideas please.

---

### Post by gezzabob on 2006-02-04
.....more info I am running Ubuntu BB 5.10.....

---

### Post by gezzabob on 2006-02-04
no just found out that the /dev/sda6 isnt my usb pen because I have not got my pen in.  It is 8MB on my sata drive so ignore the /dev/sda6 bit

---

### Post by gezzabob on 2006-02-06
OK I have stripped my PC down and re-installed the hard disk drives and Ubuntu a fresh here is my current situation....

I have the GA-7NNXP mobo with the extra IDE's and I am having trouble with the extra ide channels.

My set up is 2 x cdrom on ide 0
1 sata hdd on /dev/sda
2 x ata hdd on ide 1 /dev/hda and /dev/hdb

And 2 extra ata hdd on ide 2 The GigaRAID connections but linux is unable to see them I am trying to find drivers / setting to be able to use these extra drives.

I am running Ubuntu Breezy Badger 5.10
uname -a = Linux Ubuntu 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 i686 GNU/Linux

Can/will anybody point me in the right direction I am trying to get linux to see them so therefor used my extra 2 hdd attached to the GigaRAID.

The 2 extra drives are both matrix 120 gig ata drives. Now they are connected via ide 2 (ide 0 = 2xcdrom ide1=2xhdd and 1xsata on the sata connection).

the mobo specs are as per the gigabyte website...

Processor

1. Socket A for AMD AthlonXP / Athlon / Duron processor

Chipset

1. NVIDIA nForce2 Ultra 400 System Platform Processor (SPP)
2. Media and Communications Processor - Turbo (MCP-T)
3. Super I/O: ITE IT8712F chip
4. Silicon Image sil3112A controller
5. GigaRAID ATA 133 RAID controller
6. Intel 82540EM Gigabit LAN chip
7. Realtek 8201 LAN PHY Chip
8. Realtek ALC650/655 Audio AC'97 Codec
9. 2 x 4M bit flash ROM

Front Side Bus

1. 400/333/266 MHz FSB

Memory

1. Type Dual Channel DDR400/ 333/ 266- 184pin
2. Max capacity: Up to 3GB by 4 DIMM slots

Internal I/O Connectors

1. 2 x Serial ATA connector
2. 4 x UDMA ATA 133/100/66 Bus Master IDE connectors
3. 1 x FDD connector
4. 1 x USB 2.0/1.1 connectors(support 2 ports)
5. 2 x IEEE 1394 connectors ( supports 3 ports)
6. S/P DIF input/output pin header
7. 3 x cooling fan pin headers
8. WOL pin header
9. CD/AUX in
10. 1 x Game/Midi connector

Now all that info isnt needed but it is there to give somebody an idea what I am dealing with.

I have tried a complete re-installs of Ubuntu and so at present my system is a standard Ubuntu install with updates via apt-get.

PS the drives work in windows XP ok so not a hardware problem just a simple case of software drivers and settings.

I am not a noob but not exactly a guru either this one has stumpted me cannot seem to find out where to start with these. I have checked gigabytes website but they do not offer linux driver as far as I can tell. Nvidia offer linux driver but they only seem to be for the sound and LAN.

Please I would like to get these drives working under linux first as normal ata drive so I can re-arrange the files onto other drives then turn them into a raid array for mass storage etc.


output from various commants are..

~$ mount

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/sda1 on /boot type ext2 (rw)
/dev/hda1 on /home type ext3 (rw)
/dev/hdb1 on /media/hdb1 type vfat (rw)
/dev/hdb2 on /media/hdb2 type ext3 (rw)
/dev/hda2 on /shared32 type vfat (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4863    39062016   83  Linux
/dev/hda2            4864        9730    39094177+   b  W95 FAT32

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3902    31342783+   c  W95 FAT32 (LBA)
/dev/hdb2   *        3903       19079   121909252+  83  Linux
/dev/hdb3           19080       19457     3036285    5  Extended
/dev/hdb5           19080       19457     3036253+  82  Linux swap / Solaris

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  83  Linux
/dev/sda2               7         371     2931862+  82  Linux swap / Solaris
/dev/sda3             372        4500    33166192+  83  Linux

~$ df -H

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3               34G   3.2G    29G  10% /
tmpfs                  531M      0   531M   0% /dev/shm
tmpfs                  531M    13M   518M   3% /lib/modules/2.6.12-10-386/volatile
/dev/sda1               47M    16M    29M  36% /boot
/dev/hda1               40G   308M    38G   1% /home
/dev/hdb1               33G    23G   9.3G  72% /media/hdb1
/dev/hdb2              123G    91G    27G  78% /media/hdb2
/dev/hda2               41G    33k    41G   1% /shared32


I hope this is a bit clearer to understand.

---

### Post by gezzabob on 2006-02-11
I now can see my extra hard drives thanks to the help of these two threads

[http://ubuntuforums.org/showthread.php?t=85064&highlight=GigaRAID](http://ubuntuforums.org/showthread.php?t=85064&highlight=GigaRAID) = This one I started to configure the kernel but found it still didnt support IT8212 etc so did a search for patches etc cannot remember now what the search was but anyway found this thread

[http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12](http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12)

And it worked like a charm I have now rebooted into the new kernel and can see my extra hard drives on the gigaRAID connection.


Many thanks to both tseliot and jimbosyn for posting them very helpfull threads.......


BIG UP TO UBUNTU !!!!!:KS :) \\:D/ :-D :cool: :p 

As you can tell I am happy :-D

---

### Post by DrMalba on 2006-02-21
I am actually having a similar problem with my stock Ubuntu 2.6.10 64-bit kernel and two Western Digital 160-gig SATA drives.  I was running them with SuSE 10 previous to experimenting with Ubuntu just fine.  My dmesg is excerpted below:

[   23.622361] SCSI subsystem initialized
[   23.623171] libata version 1.11 loaded.
[   23.624058] sata_nv version 0.6
[   23.624517] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   23.624523] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 23
[   23.624536] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   23.624563] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xD000 irq 23
[   23.624578] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xD008 irq 23
[   23.978945] ata1: dev 0 cfg 49:2f00 82:346b 83:7f61 84:4003 85:3468 86:3e41 87:4003 88:407f
[   23.978948] ata1: dev 0 ATA, max UDMA/133, 312581808 sectors: lba48
[   23.980243] nv_sata: Primary device added
[   23.980244] nv_sata: Primary device removed
[   23.980246] nv_sata: Secondary device added
[   23.980247] nv_sata: Secondary device removed
[   23.980249] ata1: dev 0 configured for UDMA/133
[   23.980252] scsi0 : sata_nv
[   24.334836] ata2: dev 0 cfg 49:2f00 82:346b 83:7f61 84:4003 85:3468 86:3e41 87:4003 88:407f
[   24.334839] ata2: dev 0 ATA, max UDMA/133, 312581808 sectors: lba48
[   24.336127] nv_sata: Primary device added
[   24.336129] nv_sata: Primary device removed
[   24.336130] nv_sata: Secondary device added
[   24.336132] nv_sata: Secondary device removed
[   24.336134] ata2: dev 0 configured for UDMA/133
[   24.336136] scsi1 : sata_nv
[   24.336197]   Vendor: ATA       Model: WDC WD1600JD-98H  Rev: 08.0
[   24.336202]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   24.336546]   Vendor: ATA       Model: WDC WD1600JD-98H  Rev: 08.0
[   24.336551]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   24.337276] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[   24.337280] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 22
[   24.337287] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   24.337303] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xE400 irq 22
[   24.337319] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xE408 irq 22
[   24.537691] ata3: no device found (phy stat 00000000)
[   24.537693] scsi2 : sata_nv
[   24.738631] ata4: no device found (phy stat 00000000)
[   24.738633] scsi3 : sata_nv

after my IDE and CDROM are probed, this pops up:
[   28.610716] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   28.610724] SCSI device sda: drive cache: write back
[   28.610768] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   28.610774] SCSI device sda: drive cache: write back
[   28.610777]  /dev/scsi/host0/bus0/target0/lun0: p1
[   28.633073] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[   28.633084] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   28.633091] SCSI device sdb: drive cache: write back
[   28.633122] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   28.633128] SCSI device sdb: drive cache: write back
[   28.633130]  /dev/scsi/host1/bus0/target0/lun0: p1
[   28.639313] Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
[   28.827328] Attempting manual resume
[   28.830942] swsusp: Suspend partition has wrong signature?

Later the raid driver has some mysterious output as well:


[   32.079233] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   32.081694] md: raid0 personality registered as nr 2
[   32.162842] devfs_mk_dev: could not append to parent for md/0
[   32.164400] md: md0 stopped.
[   32.164778] md: bind<sda1>
[   32.190129] Attempting manual resume
[   32.190212] swsusp: Suspend partition has wrong signature?
[   32.212381] kjournald starting.  Commit interval 5 seconds
[   32.212390] EXT3-fs: mounted filesystem with ordered data mode.
[   33.477405] md: md0 stopped.
[   33.477409] md: unbind<sda1>
[   33.477411] md: export_rdev(sda1)
[   33.477810] md: bind<sda1>


The result is Ubuntu refuses to mount my SATA drives at boottime, or manually from the command line, claiming the devices are busy.  Any ideas?

My config:

Gigabyte GA-K8N-SLI mobo,  AMD Athlon 3700+  1gig RAM
Gigabyte GB-NX66L128DP PCIE display card (GeForce 6600LE chipset)
single WD 250 gig IDE drive (contains root partition)
Dual WD 160-gig SATA drives (no raid, ext3 formatted)

I also have an older PCI 3c590 card in there as well.

---

