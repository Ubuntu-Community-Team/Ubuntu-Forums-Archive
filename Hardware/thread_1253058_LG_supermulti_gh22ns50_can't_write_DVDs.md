---
title: "LG supermulti gh22ns50 can't write DVDs"
date: 2009-08-29
forum: Hardware
---

### Post by vexorian on 2009-08-29
I just installed a new burner over my old DVD burner + CD burner combo. 

The problem is that now neither k3b or brasero are able to burn DVDs. It is a very strange issue, they are able to burn CDs, and when I pick to simulate the process, it works. But when doing the actual writing, both stay idle for a while and then k3b says : "Write Error" and brasero says "unknown error" then when I read the resulting, unusable DVD disk, there are all the files I tried to write on the DVD , but they are cause I/O errors when trying to read them.


edit: nope, not even nero linux can burn :(

I had to go through the humiliating process of booting to windows, installed the Nero that came with the burner, and it can burn DVDs normally.

Not sure what could I do here.

edit: the log:
```

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-15-generic
Devices
-----------------------
HL-DT-ST DVDRAM GH22NS50 TN01 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 8.2x1352KBps.
:-[ WRITE@LBA=1b0h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
:-( write failed: Invalid argument
/dev/sr0: flushing cache
/dev/sr0: updating RMA
/dev/sr0: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:476 -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m 


```

---

### Post by vexorian on 2009-08-29
I 'solved' it by installing the Nero that came with the drive's CD into virtualbox, so I can at least burn images from virtual Box, it is kind of lame to boot a whole VM for this.

Really wish to find an actual solution that allowed me to keep using k3b :(

---

### Post by vexorian on 2009-08-30
ok... I solved the problem by... adding a 20GB swap partition.

Before this incident, I was completely fine burning DVDs with no swap partition at all.

Not even very small iso files would burn.

I don't get exactly why this worked, but at least it did...

---

### Post by Katai on 2010-02-27
Sorry for revive an old thread, but I'm trying to get the same burner to work. Did you discover anything else in this months ? I'll go to buy some dvd and try the swap thing later.

---

### Post by JB's on 2010-03-02
Hi,
I have the same  problem...
I tried to create a swap partition (20GB) but does not work..

PS: sorry for my bad English :)

---

### Post by carlosbellino on 2010-03-26
Hi, try cheking that you DVD-writer have "pata_atiixp driver" with
command "[FONT=monospace]dmesg | grep scsi[0-7]"[/FONT]
_________________________________________________________________________
[FONT=monospace]kaname@kaname-desktop:~$ dmesg | grep scsi[0-7]
[    1.274677] scsi0 : ahci
[    1.274727] scsi1 : ahci
[    1.274757] scsi2 : ahci
[    1.274785] scsi3 : ahci
[COLOR=Red][    1.275092] scsi4 : pata_atiixp
[    1.275120] scsi5 : pata_atiixp[/COLOR]
[    2.079988] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.379864] scsi6 : SCSI emulation for USB Mass Storage devices
__________________________________________________________________________

Sata Channels 4 and 5 have it,
Verify where is your burner:
"dmesg | grep scsi | grep GH22NS50"

[/FONT][FONT=monospace]__________________________________________________________________________

kaname@kaname-desktop:~$ dmesg | grep scsi | grep GH22NS50
[    2.058836] [COLOR=Red]scsi 2[/COLOR]:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[/FONT][FONT=monospace]__________________________________________________________________________
[/FONT]
[FONT=monospace]and [/FONT]then at the mobo plug the SATA cable on 4th or 5th sata channel..

---

### Post by JB's on 2010-03-30
Hi, carlosbellino

I have my DVD-burner on channel 2

```
dmesg | grep scsi | grep GH22NS50
```

[    1.580915] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5

```
dmesg | grep scsi[0-7]
```

[    1.081379] scsi0 : ahci
[    1.081442] scsi1 : ahci
[    1.081487] scsi2 : ahci
[    1.081523] scsi3 : ahci
[    1.081560] scsi4 : ahci
[    1.081598] scsi5 : ahci
[    1.081932] scsi6 : pata_amd
[    1.081969] scsi7 : pata_amd
[    1.601883] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray


I move the connector on channel 6 or 7?

PS:
This is my motherboard: [http://pic.xfastest.com/sxs112/ASUS/M3N78-VM/01.jpg](http://pic.xfastest.com/sxs112/ASUS/M3N78-VM/01.jpg)

I see only n°5 port + n°1 external  ???  
(my motherboard supports SATA only on channels 1-2-3)

Thanks :)

---

### Post by slazil on 2010-04-01
Hi !

I encountered the same problem with my GH22ns50.
I have G43T-M pro MB and SATA HDD.
Firstly I configured SATA as AHCI in BIOS and got the subject.
Now I tried configure SATA as IDE, and have connected GH22NS50 to sata ch.#2
and now it works perfectly.

I have just burned a disk with GnomeBaker.

Hope this would help.

Ilya.

---

### Post by josephitaly on 2010-04-02
hi slazil i have tried to change bios to ahci;now, how can i change cofiguration from sata to ide?

---

### Post by JB's on 2010-04-11
Hi

I have update to Lucid 10.04 and the dvd burner works!

---

### Post by Ellume on 2010-05-09
I was also having the same problem on 9.1. After updating to 10.04 the burner is working.

---

### Post by zolki on 2010-05-23
I can confirm this problem. I was having it with 8.10 (kernel 2.6.27-7) and also now with 10.04 (2.6.32-22). I am using the GH22NS50 device through SATA Promise PCI card. It reads DVDs well, writes CDs not very well (in K3B only at approx 1.5x speed or so independent on the chosen speed in the dialog box) and does not write DVDs at all. The key word in the K3B log (see below) is:
```
:-[ WRITE@LBA=130h failed with SK=7h/NO ADDITIONAL SENSE INFORMATION]: Input/output error
:-( write failed: Input/output error

```Similar problem occurs while working directly with growisofs or wodim (in wodim the dev=x,y,z syntax does not work for me, since it is through external card, it only works with dev=/dev/scd0). I tried ISOBURN under wine, it even burns the DVD, but with several systematic errors (sector not found, retrying etc.) and afterwards some of the files on DVD are unreadable. No wonder, if it is a kernel and GH22NS50 incompatibility problem, then ISOBURN may well retry if could not burn a sector once, but this is an abnormal way of burning something to my mind.

I don't know what to do next. As there are people mostly having similar problems also with firmware TN02, the update on that should not work. Perhaps the best is to wait and hope that somebody who knows what is going on (Jörg Schilling or someone else) will give an improvement into the next revision of the kernel...

uname -a:
```
Linux zolki-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
```sudo /sbin/hdparm -I /dev/sr0
```
/dev/sr0:

ATAPI CD-ROM, with removable media
        Model Number:       HL-DT-ST DVDRAM GH22NS50                
        Serial Number:      K00262J4319         
        Firmware Revision:  TN01    
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(can be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
```relevant lines from dmesg:
```
sata_promise 0000:00:0b.0: version 2.12
sata_promise 0000:00:0b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
ata1: SATA max UDMA/133 mmio m4096@0xe6020000 ata 0xe6020200 irq 18
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100
scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
```the k3b error log:
```
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.32-22-generic
Devices
-----------------------
HL-DT-ST CD-RW GCE-8520B 1.03 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

HL-DT-ST DVDRAM GH22NS50 TN01 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R jÃ¤rjestikune, DVD-R kahekihiline jÃ¤rjestikune, DVD-R kahekihiline hÃ¼petega, DVD-RAM, DVD-RW piiratud Ã¼lekirjutamisega, DVD-RW jÃ¤rjestikune, DVD+RW, DVD+R, DVD+R kahekihiline, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Piiratud Ã¼lekirjutamine, Kahekihiline hÃ¼petega]
Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 2214878 (4536070144 bytes)
Pipe throughput: 34303648 bytes read, 34283168 bytes written.

Used versions
-----------------------
mkisofs: 1.1.8
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 4.1x1352KBps.
          0/4536070144 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4536070144 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4536070144 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4536070144 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=130h failed with SK=7h/NO ADDITIONAL SENSE INFORMATION]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: closing track
/dev/scd0: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2214878 -dvd-compat -speed=4 -overburn -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2214878
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using A000.;1 for  internet/protokollid_files/a. (a)
  0.02% done, estimate finish Sun May 23 11:14:30 2010
  0.05% done, estimate finish Sun May 23 11:14:30 2010
  0.07% done, estimate finish Sun May 23 11:14:30 2010
  0.09% done, estimate finish Sun May 23 11:14:30 2010
  0.11% done, estimate finish Sun May 23 11:14:30 2010
  0.14% done, estimate finish Sun May 23 11:14:30 2010
  0.16% done, estimate finish Sun May 23 11:14:30 2010
  0.18% done, estimate finish Sun May 23 11:14:30 2010
  0.20% done, estimate finish Sun May 23 11:14:30 2010
  0.23% done, estimate finish Sun May 23 11:14:30 2010
  0.25% done, estimate finish Sun May 23 11:14:30 2010
  0.27% done, estimate finish Sun May 23 11:14:30 2010
  0.29% done, estimate finish Sun May 23 11:14:30 2010
  0.32% done, estimate finish Sun May 23 11:14:30 2010
  0.34% done, estimate finish Sun May 23 11:14:30 2010
  0.36% done, estimate finish Sun May 23 11:14:30 2010
  0.38% done, estimate finish Sun May 23 11:14:30 2010
  0.41% done, estimate finish Sun May 23 11:14:30 2010
  0.43% done, estimate finish Sun May 23 11:14:30 2010
  0.45% done, estimate finish Sun May 23 11:14:30 2010
  0.47% done, estimate finish Sun May 23 11:14:30 2010
  0.50% done, estimate finish Sun May 23 11:14:30 2010
  0.52% done, estimate finish Sun May 23 11:14:30 2010
  0.54% done, estimate finish Sun May 23 11:14:30 2010
  0.56% done, estimate finish Sun May 23 11:14:30 2010
  0.59% done, estimate finish Sun May 23 11:14:30 2010
  0.61% done, estimate finish Sun May 23 11:14:30 2010
  0.63% done, estimate finish Sun May 23 11:14:30 2010
  0.66% done, estimate finish Sun May 23 11:17:02 2010
  0.68% done, estimate finish Sun May 23 11:16:57 2010
  0.70% done, estimate finish Sun May 23 11:16:52 2010
  0.72% done, estimate finish Sun May 23 11:16:48 2010
  0.75% done, estimate finish Sun May 23 11:54:45 2010

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid asjad -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-zolkiwpjTvg/k3bsh5Tsa.tmp -rational-rock -hide-list /tmp/kde-zolkiwpjTvg/k3bUk6rVa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-zolkiwpjTvg/k3b3tAISa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-zolkiwpjTvg/k3b83IhMb.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid asjad -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-zolkiwpjTvg/k3bGM2eDa.tmp -rational-rock -hide-list /tmp/kde-zolkiwpjTvg/k3bScWN3a.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-zolkiwpjTvg/k3bUwkT9b.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-zolkiwpjTvg/k3bG4QkKa.tmp 

```

---

### Post by alejandro.mc on 2010-05-28
I have the same LG and have just installed 10.04, and it can read blanc cd/dvds, burn them, but I still can't READ dual layer dvds, I can burn them succesfully though..

Know anything about this?

Thanks

---

### Post by offmessage on 2010-07-26
I have an LG supermulti gh22ns40 installed in a machine running a clean Lucid installation and I cannot read dual layer DVDs.

Any advice would be greatly appreciated!

---

### Post by siddhartha007 on 2010-10-13
Hello guys.
I'm a user of the french forum, but I come to see and ask you about the problem described here: did Lucid or Maverick solve it? I'm about to buy a burner, this one seemed fine but I need to check everything's okay.

Thanks

siddhartha

---

### Post by pros on 2010-10-13
Yes, seems this problem is resolved.

Anyway, if i had to buy a new burner knowing about this situation,
LG products would be the last to consider.

Vendors, have to convince us about their product compatibility, not the other way around!
I value my time, and i do not want to spend it on LG incompatibilities again!

---

### Post by vexorian on 2010-10-14
Great news if maverick fixed it , I am just upgrading right now, let's see if it does it.

Regarding the swap partition 'fix' it was very strange because it started to stop working after a while. In fact, it works some times. I have no idea why it works some times and why it doesn't other times...

---

