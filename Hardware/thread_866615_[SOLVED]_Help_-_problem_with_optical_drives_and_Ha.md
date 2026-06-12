---
title: "[SOLVED] Help - problem with optical drives and Hardy"
date: 2008-07-22
forum: Hardware
---

### Post by dustigroove on 2008-07-22
Okay, so typically when I run into any troubles I am able to search through the forums or Google to find the answers myself... this time around I'm posting a request for help.
 
 *The scenario*:
 
 I have had Ubuntu installed on this particular home PC since Dapper, upgraded to Gutsy (fresh install), and then just recently completed a clean install of Hardy. With Dapper and Gutsy I had no major issues with the machine, and other than personal tweaking really had a nice turn-key system up and running right from the get-go.
 
 However it appears that something isn't playing nice between Hardy and my two optical drives, an ASUS DRW-1608P and an ASUS DRW-1814BL. Now I am unable to successfully burn any discs (getting overburn errors) and generally accessing discs in the drive usually results in the drive locking up in a read state.
 
 Messages shown during one of these lockups (from dmesg) shows:
 
 ```
r 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
 [ 1543.591681] end_request: I/O error, dev sr1, sector 9852
 [ 1543.604201] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
 [ 1543.604208] sr 1:0:1:0: [sr1] Sense Key : Hardware Error [current] 
 [ 1543.604211] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
 [ 1543.604215] end_request: I/O error, dev sr1, sector 9852
``` This pretty much repeats indefinitely and pressing the eject button or doing an unmount fail with a 'device is busy' message.

Since I've lucked out and had no issues with this in the past, I'm a bit at a loss as to how to tackle this one... HELP!

Thanks in advance,

---

### Post by dustigroove on 2008-07-22
Some further exploration and here are my findings... that I truly know not what to do with. I don't see anything that screams FIX ME, I'M YOUR ISSUE!

[php]$ ls -l /dev/cd*
lrwxrwxrwx 1 root root 4 2008-07-22 12:17 /dev/cdrom -> scd1
lrwxrwxrwx 1 root root 4 2008-07-22 12:17 /dev/cdrom1 -> scd0
lrwxrwxrwx 1 root root 4 2008-07-22 12:17 /dev/cdrw -> scd1
lrwxrwxrwx 1 root root 4 2008-07-22 12:17 /dev/cdrw1 -> scd0[/php][php]$ ls -l /dev/sc*
brw-rw----+ 1 root cdrom 11, 0 2008-07-22 08:17 /dev/scd0
brw-rw----+ 1 root cdrom 11, 1 2008-07-22 08:17 /dev/scd1[/php][php]$ dmesg | grep ROM
[   32.206122] scsi 1:0:0:0: CD-ROM            ASUS     DRW-1608P        1.40 PQ: 0 ANSI: 5
[   32.206619] scsi 1:0:1:0: CD-ROM            ASUS     DRW-1814BL       1.10 PQ: 0 ANSI: 5
[   32.354729] Uniform CD-ROM driver Revision: 3.20
[   32.354779] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   32.358584] sr 1:0:1:0: Attached scsi CD-ROM sr1[/php][php]$ wodim -scanbus
scsibus1:
        1,0,0   100) 'ASUS    ' 'DRW-1608P       ' '1.40' Removable CD-ROM
        1,1,0   101) 'ASUS    ' 'DRW-1814BL      ' '1.10' Removable CD-ROM
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *[/php][php]$ sudo lshw -C disk
  *-cdrom:0
       description: DVD writer
       product: DRW-1608P
       vendor: ASUS
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.40
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD-RAM writer
       product: DRW-1814BL
       vendor: ASUS
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open[/php][php]$ sudo hdparm -i /dev/cdrom1

/dev/cdrom1:

 Model=ASUS    DRW-1608P                       , FwRev=1.40    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode[/php][php]$ sudo hdparm -i /dev/cdrom

/dev/cdrom:

 Model=ASUS    DRW-1814BL                      , FwRev=1.10    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode[/php]Perhaps someone else can read something out of this that I am missing?

---

### Post by dustigroove on 2008-07-22
Okay, so it seems that I can burn a CD successfully from within the Gutsy live cd environment, but not from within the Hardy live cd or Hardy itself. The main difference that I note after grabbing info from each is that Hardy assigns the optical drives as SCSI devices, /dev/scd*, while Gutsy assigns them logical names conforming to the /dev/hd* format.

Any suggestions? I'm beginning to feel like a community of one here...

Info under Gutsy Live CD:
[php]$ ls -l /dev/hd* | grep -i rom
brw-rw---- 1 root cdrom 22,  0 2008-07-22 14:24 /dev/hdc
brw-rw---- 1 root cdrom 22, 64 2008-07-22 14:24 /dev/hdd

$ ls -l /dev/hd* | grep -i rom
brw-rw---- 1 root cdrom 22,  0 2008-07-22 14:24 /dev/hdc
brw-rw---- 1 root cdrom 22, 64 2008-07-22 14:24 /dev/hdd

$ dmesg | grep ROM
[   39.408144] hdc: ASUS DRW-1608P, ATAPI CD/DVD-ROM drive
[   40.191528] hdd: ASUS DRW-1814BL, ATAPI CD/DVD-ROM drive
[   40.327825] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[   40.327832] Uniform CD-ROM driver Revision: 3.20
[   40.700662] hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)

$ wodim -scanbus
scsibus1000:
        1000,0,0 100000) *
        1000,1,0 100001) *
        1000,2,0 100002) *
        1000,3,0 100003) 'ASUS    ' 'DRW-1814BL      ' '1.10' Removable CD-ROM
        1000,4,0 100004) *
        1000,5,0 100005) *
        1000,6,0 100006) *
        1000,7,0 100007) *

$ sudo lshw -C disk
  *-cdrom:0
       description: DVD writer
       product: ASUS DRW-1608P
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 1.40
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma4 status=ready
     *-disc
          physical id: 0
          logical name: /dev/hdc
  *-cdrom:1
       description: DVD-RAM writer
       product: ASUS DRW-1814BL
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: 1.10
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc

$ sudo hdparm -i /dev/cdrom

/dev/cdrom:

 Model=ASUS DRW-1608P, FwRev=1.40, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode

$ sudo hdparm -i /dev/cdrom1

/dev/cdrom1:

 Model=ASUS DRW-1814BL, FwRev=1.10, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode[/php]Info under Hardy Live CD:
[php]$ ls -l /dev/cd*
lrwxrwxrwx 1 root root 4 2008-07-22 14:52 /dev/cdrom -> scd0
lrwxrwxrwx 1 root root 4 2008-07-22 14:52 /dev/cdrom1 -> scd1
lrwxrwxrwx 1 root root 4 2008-07-22 14:52 /dev/cdrw -> scd0
lrwxrwxrwx 1 root root 4 2008-07-22 14:52 /dev/cdrw1 -> scd1

$ ls -l /dev/sc*
brw-rw----+ 1 root cdrom 11, 0 2008-07-22 14:51 /dev/scd0
brw-rw----+ 1 root cdrom 11, 1 2008-07-22 14:51 /dev/scd1

$ dmesg | grep ROM
[   41.424305] scsi 1:0:0:0: CD-ROM            ASUS     DRW-1608P        1.40 PQ: 0 ANSI: 5
[   41.424807] scsi 1:0:1:0: CD-ROM            ASUS     DRW-1814BL       1.10 PQ: 0 ANSI: 5
[   41.493605] Uniform CD-ROM driver Revision: 3.20
[   41.493650] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   41.497425] sr 1:0:1:0: Attached scsi CD-ROM sr1

$ wodim -scanbus
scsibus1:
    1,0,0    100) *
    1,1,0    101) 'ASUS    ' 'DRW-1814BL      ' '1.10' Removable CD-ROM
    1,2,0    102) *
    1,3,0    103) *
    1,4,0    104) *
    1,5,0    105) *
    1,6,0    106) *
    1,7,0    107) *

$ sudo lshw -C disk
  *-cdrom:0
       description: DVD writer
       product: DRW-1608P
       vendor: ASUS
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: 1.40
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
  *-cdrom:1
       description: DVD-RAM writer
       product: DRW-1814BL
       vendor: ASUS
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open

$ sudo hdparm -i /dev/cdrom

/dev/cdrom:

 Model=ASUS    DRW-1608P                       , FwRev=1.40    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode

$ sudo hdparm -i /dev/cdrom1

/dev/cdrom1:

 Model=ASUS    DRW-1814BL                      , FwRev=1.10    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode[/php]Thanks,

---

### Post by dustigroove on 2008-07-24
So I take it there are no kind souls here with any knowledge of this topic to lend a hand? It would be a shame to have to jump ship for something as basic as getting a couple of optical drives working...

---

### Post by tackfurlo on 2008-07-24
I'm at a bit of a loss myself as I have several systems with DVD burners and all of them show the burner as /dev/hd* so I don't know.  My best ***guess*** is that maybe you should clock them down from UDMA4 to maybe UDMA2 or some slower Bbus speed, though again, that's just a guess, and I also don't know how to do that.

Beypond that, I'm all out.

I have a friend with a brand new desktop.  It came with Vista and he still runs Vista on it but runs Xubuntu on his laptop and would run the same on his new desktop except he uses it mostly as a gaming box.  I will get him to boot to a LiveCD and see what his system detects his burner as, but I can't promise how quickly he'll do it.  He was about to begin a new Xubuntu install on his laptop about 2 hours ago (He's been using plain old Ubuntu until today) so he may not have wifi up on his laptop yet and if he doesn't he'll have no way to chat with me once he tries booting his desktop from the LiveCD.

---

### Post by tackfurlo on 2008-07-24
Ok, my friend is downloading a Hardy ISO and will check this out for you to see how his is detected, if he can burn a DVD, and if so, what UDMA level he has set.  I'll let you know what he finds out...in 2 or 3 hours.

---

### Post by dustigroove on 2008-07-25
Appreciate trying to help, thank you...

---

### Post by dustigroove on 2008-08-26
:KS BUMP :KS

I really could use a hand here folks! Thanks.

---

### Post by dustigroove on 2008-08-26
Marking thread as solved due to no help being received... no sense in leaving it open to languish.  :-|

[COLOR=Blue]**Feel free to PM me if there are any helpful souls that come across this with any wisdom or answers.**[/COLOR]

---

