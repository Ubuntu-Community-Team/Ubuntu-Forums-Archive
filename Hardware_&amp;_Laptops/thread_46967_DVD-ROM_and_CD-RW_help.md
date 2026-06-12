---
title: "DVD-ROM and CD-RW help"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by vander on 2005-07-06
So, a couple of weeks back I was copying a file from a DVD and started a second file at the same time using xwindows (not command line).  The copying froze for both files, and I haven't been able to get my DVD-ROM (SAMSUNG DVD-ROM SD-616T) working again nor can I read files from my CD-RW (HL-DT-ST GCE-8481B) either.  

After I insert a CD it will read the table of contents and display them, but it won't play CDs or copy files from a CD or DVD.  The CD-RW will write CDs but won't play them either.

My friend tells me my hardware is failing, but I refuse to believe that since the read problem is happening to both of the drives.

thanks for your help.

here's the output from $dmesg|grep ^hd  :

hda: WDC WD1200JB-75CRA0, ATA DISK drive
hdb: Maxtor 5A300J0, ATA DISK drive
hda: max request size: 128KiB
hda: Host Protected Area detected.
hda: Host Protected Area disabled.
hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes not supported
hdb: max request size: 1024KiB
hdb: 585940320 sectors (300001 MB) w/2048KiB Cache, CHS=36473/255/63, UDMA(100)
hdb: cache flushes supported
hdc: SAMSUNG DVD-ROM SD-616T, ATAPI CD/DVD-ROM drive
hdd: HL-DT-ST GCE-8481B, ATAPI CD/DVD-ROM drive
hdc: ATAPI 48X DVD-ROM drive, 512kB Cache
hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache
hdc: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
hdc: set_drive_speed_status: error=0x00

---

