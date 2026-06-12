---
title: "Ubuntu won't read encrypted DVD"
date: 2011-04-18
forum: Hardware
---

### Post by WhiteHorse on 2011-04-18
Hi all, I've tried everything in the forums to get my DVD drive to read encrypted dvds including:
1. Install deCSS
2. Install and set region
3. Install restricted formats
4. Change BIOS setting from AHCI to IDE mode

Nothing seems to work. I get no dmesg output. CDs, unencrypted DVDs and data CDs and data DVDs work just fine.
Running > sudo lshw -C disk gives

*-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GSA-T20N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: WP03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
> uname -r gives
2.6.35-28-generic

The dmesg startup logs show
[    0.686044] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.686052] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701f270), AE_NOT_FOUND
[    1.054657] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WP03 PQ: 0 ANSI: 5
[    1.058058] sr0: scsi3-mmc drive: 31x/31x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.058062] Uniform CD-ROM driver Revision: 3.20
[    1.058195] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.058266] sr 0:0:0:0: Attached scsi generic sg0 type 5


> sudo hdparm -i /dev/scd0 gives:

/dev/scd0:

 Model=HL-DT-ST DVDRAM GSA-T20N, FwRev=WP03, SerialNo=KZ17C705226
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=unknown, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

---

