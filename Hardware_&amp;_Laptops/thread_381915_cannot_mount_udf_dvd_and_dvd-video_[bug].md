---
title: "cannot mount udf dvd and dvd-video [bug?]"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by iDleR on 2007-03-11
I've downloaded yesterday the alternate-cd of ubuntu edgy. I've installed it but I have a problem. I cannot mount dvd.
This is my fstab:
```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This is my /proc/filesystem
```

dierre@elliot:~$ cat /proc/filesystems | grep udf
        udf

```

When I try to mount a dvd this is the error:
```

mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

```

These dvds works on debian so it's an ubuntu problem.

---

### Post by iDleR on 2007-03-11
I've forgot to tell that it's not working also using root command "mount -t udf /dev/hdc/ /media/cdrom0", the log says:

```

root@elliot:~# dmesg | tail
[17192206.048000] end_request: I/O error, dev hdc, sector 6882348
[17192206.056000] hdc: tray open
[17192206.056000] end_request: I/O error, dev hdc, sector 6881324
[17192206.060000] hdc: tray open
[17192206.060000] end_request: I/O error, dev hdc, sector 6881100
[17192206.068000] hdc: tray open
[17192206.068000] end_request: I/O error, dev hdc, sector 1248
[17192206.072000] hdc: tray open
[17192206.072000] end_request: I/O error, dev hdc, sector 1024
[17192206.072000] UDF-fs: No partition found (1)

```

and I think the module it's correctly up
```

root@elliot:~# modprobe -l|grep udf
/lib/modules/2.6.17-11-generic/kernel/fs/udf/udf.ko

```

---

### Post by iDleR on 2007-03-11
I think I will recompile a kernel source.
See the hdparm infos:
```

dierre@elliot:~$ sudo hdparm -i /dev/hdc

/dev/hdc:

 Model=PIONEER DVD-RW DVR-107D, FwRev=1.10, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode

```

```

dierre@elliot:~$ sudo hdparm -I /dev/hdc

/dev/hdc:

ATAPI CD-ROM, with removable media
        Model Number:       PIONEER DVD-RW  DVR-107D
        Serial Number:      DBDL150056WL
        Firmware Revision:  1.10
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(can be disabled)
        Buffer size: 64.0kB
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    Power Management feature set
           *    PACKET command feature set
           *    DEVICE_RESET command
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper

```

---

### Post by iDleR on 2007-03-12
up

---

### Post by iDleR on 2007-03-12
up

---

### Post by iDleR on 2007-03-13
up

---

