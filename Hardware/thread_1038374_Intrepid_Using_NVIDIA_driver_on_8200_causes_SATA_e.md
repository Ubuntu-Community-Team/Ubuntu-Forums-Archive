---
title: "Intrepid: Using NVIDIA driver on 8200 causes SATA errors?"
date: 2009-01-12
forum: Hardware
---

### Post by ozra on 2009-01-12
*Apologies if doing it incorrectly, I should have posted this in this hardware forum instead of in General Help.*

Good day everybody.

Has anybody encountered SATA errors when they load the Proprietary 173 or 177 NVIDIA drivers? The same happens with NVIDIA binary drivers 180.11 / 180.18 and 180.22.

The errors disappear if loading the native Ubuntu Intrepid VESA driver instead of the NVIDIA supplied binary/proprietary driver.

Symptoms:

I noticed "hard resetting link" and SError: { Handshk } SATA errors in dmesg on my Intrepid 8.10 2.6.27-11-generic up to date on 12 Jan 2009 Ubuntu box. (Desktop i386)

It is a Nvidia 8200 Gigabyte GA-M78SM-S2H motherboard (latest Bios installed today). 4 gig Ram. AMD x2 3000 MHz CPU. 1 x 300GB Maxtor SATA HD (sda) + 2 x 750GB Western Digital SATA HD's (sdb and sdc). Pioneer SATA DVD writer.

I have apt-get install bonnie to test my HD's

I have the latest NVIDIA binary 180.22 driver installed.

Running bonnie via terminal window in GDM to exercise my HD's I will see dmesg running lots of the following errors ONLY for the two 750 GB HD's (/dev/sdb and /dev/sdc )(no errors get logged for /dev/sda):

[ 247.123447] ata2.00: exception Emask 0x10 SAct 0x201 SErr 0x400000 action 0x6 frozen
[ 247.123452] ata2.00: irq_stat 0x08000000, interface fatal error
[ 247.123455] ata2: SError: { Handshk }
[ 247.123459] ata2.00: cmd 61/00:00:cf:ff:2e/04:00:05:00:00/40 tag 0 ncq 524288 out
[ 247.123460] res 40/00:04:cf:ff:2e/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[ 247.123462] ata2.00: status: { DRDY }
[ 247.123466] ata2.00: cmd 61/40:48:e7:05:2f/02:00:05:00:00/40 tag 9 ncq 294912 out
[ 247.123467] res 40/00:04:cf:ff:2e/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[ 247.123469] ata2.00: status: { DRDY }
[ 247.123473] ata2: hard resetting link
[ 247.604021] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 247.605562] ata2.00: configured for UDMA/133
[ 247.605575] ata2: EH complete
[ 247.605828] sd 1:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[ 247.605842] sd 1:0:0:0: [sdb] Write Protect is off
[ 247.605845] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 247.605863] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

The above is an example but gets logged for both sdb and sdc.

I bought a new PSU: Thermaltake 550W (TR2-550) to replace the 300W PSU but the above continues regardless of which PSU I use.

If I kill GDM (/etc/init.d/gdm stop) and run bonnie on either sdb or sdc or on all 3 drives (multiple terminals (F1/F2/F3 and F4 to watch dmesg / messages) simultaneously, no errors get logged. Start GDM and the errors multiply continuously. (Except for no errors on sda as stated previously)

Please note: sda1 is my boot. sdb1 is not in use but mounted /media/storage1 and sdc1 is mounted /media/storage2. sdc1 is used as myth data drive.

If I boot off the Ubuntu 8.10 i386 desktop live CD into GDM: Apt-get install bonnie etc and then run tests, no errors get logged for ANY drives.

Errors only get logged for sdb and sdc when booting off sda (sda1) and with GDM running (NVIDIA driver 180.22)

Using the VESA driver stops the SATA errors.

Installing Proprietary driver 173 or 177 causes the errors to re-appear.

Installing the binary 180.11 / 180.18 / 180.22 driver causes the errors to re-appear.

Reverting back to the VESA driver causes the errors to stop.

**Any suggestions on what I can do to stop the SATA reset errors whilst using the proprietary NVIDIA driver?**

It is a MythTV frontend so I need the 2D acceleration.

It has now started to cause file corruption on my myth data drive (sdc) fsck fixes it and it is ok for a couple of days after that until it gets too much. ONLY the 750GB drives are affected. Disabling NCQ ( $ echo 1 > /sys/block/sdb/device/queue_depth) and Write caching (hdparm -W0 /dev/sdb)on these two drives does not stop the errors either when using NVIDIA supplied drivers.

Thank You kindly.

Here is some more info:

myth@myth:~$ uname -r
2.6.27-11-generic
myth@myth:~$ sudo hdparm -i /dev/sda
[sudo] password for myth:

/dev/sda:

Model=Maxtor 6L300S0 , FwRev=BANC1G10, SerialNo=L60DMQWG
Config={ Fixed }
RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?0?
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=586114704
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio1 pio2 pio3 pio4
DMA modes: mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
AdvancedPM=yes: unknown setting WriteCache=enabled
Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0: ATA/ATAPI-1,2,3,4,5,6,7

    * signifies the current active mode

myth@myth:~$ sudo hdparm -i /dev/sdb

/dev/sdb:

Model=WDC WD7500AACS-00D6B0 , FwRev=01.01A01, SerialNo= WD-WCAU41064087
Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?0?
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1465149168
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio3 pio4
DMA modes: mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
AdvancedPM=no WriteCache=enabled
Drive conforms to: Unspecified: ATA/ATAPI-1,2,3,4,5,6,7

    * signifies the current active mode

(The above was running in udma6 mode until the errors start, then it negotiates udma5)

myth@myth:~$ sudo hdparm -i /dev/sdc

/dev/sdc:

Model=WDC WD7500AACS-00D6B0 , FwRev=01.01A01, SerialNo= WD-WCAU40908795
Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?0?
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1465149168
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio3 pio4
DMA modes: mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
AdvancedPM=no WriteCache=enabled
Drive conforms to: Unspecified: ATA/ATAPI-1,2,3,4,5,6,7

    * signifies the current active mode

myth@myth:~$
myth@myth:~$

dmesg excerpt:

[ 247.123447] ata2.00: exception Emask 0x10 SAct 0x201 SErr 0x400000 action 0x6 frozen
[ 247.123452] ata2.00: irq_stat 0x08000000, interface fatal error
[ 247.123455] ata2: SError: { Handshk }
[ 247.123459] ata2.00: cmd 61/00:00:cf:ff:2e/04:00:05:00:00/40 tag 0 ncq 524288 out
[ 247.123460] res 40/00:04:cf:ff:2e/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[ 247.123462] ata2.00: status: { DRDY }
[ 247.123466] ata2.00: cmd 61/40:48:e7:05:2f/02:00:05:00:00/40 tag 9 ncq 294912 out
[ 247.123467] res 40/00:04:cf:ff:2e/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[ 247.123469] ata2.00: status: { DRDY }
[ 247.123473] ata2: hard resetting link
[ 247.604021] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 247.605562] ata2.00: configured for UDMA/133
[ 247.605575] ata2: EH complete
[ 247.605828] sd 1:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[ 247.605842] sd 1:0:0:0: [sdb] Write Protect is off
[ 247.605845] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 247.605863] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 247.743411] ata2.00: exception Emask 0x10 SAct 0x7ffef SErr 0x400000 action 0x6 frozen

---

