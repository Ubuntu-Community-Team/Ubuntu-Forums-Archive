---
title: "strange problem with DMA"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by dukeinlondon on 2005-04-07
When I am trying to enable DMA for /dev/hda using hdparm -d1 /dev/hda

the disk operations freeze for a moment and I get that in syslogs :

Apr  8 00:17:41 localhost kernel:
Apr  8 00:17:41 localhost kernel: ide: failed opcode was: unknown
Apr  8 00:17:47 localhost kernel: hda: status timeout: status=0xd0 { Busy }
Apr  8 00:17:47 localhost kernel:
Apr  8 00:17:47 localhost kernel: ide: failed opcode was: unknown
Apr  8 00:17:47 localhost kernel: hdb: DMA disabled
Apr  8 00:17:47 localhost kernel: hda: drive not ready for command
Apr  8 00:17:47 localhost kernel: ide0: reset: success

Apr  8 00:14:07 localhost kernel: hdb: dma_timer_expiry: dma status == 0x41
Apr  8 00:14:07 localhost kernel: hdb: DMA timeout error
Apr  8 00:14:07 localhost kernel: hdb: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }

It didn't use to be a problem in the past even with kernel 2.6.6 (custom debian image)

Any idea ?

---

### Post by Bob D. on 2005-04-08
Is hda a hard drive or a optical drive on your system?

If a hard drive, I'm surprised that DMA isn't already activated...even my old P2, 233Mhz test box activated DMA for the hard drive to the max it's old chipset can support (udma2). It didn't for my old burner and CD-Rom, but I'm not even sure they support DMA.

What does hdparm -i /dev/hda show?

Thanks!

Bob

---

### Post by dukeinlondon on 2005-04-08
/dev/hda:

 Model=SAMSUNG SP1604N, FwRev=TM100-24, SerialNo=0651J1FWC03485
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode


Funny, I've used hdparm forever but never knew about the -i switch.... does it tell you anything ?

---

### Post by Bob D. on 2005-04-08
Sure does. This section:

```
UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
AdvancedPM=no WriteCache=enabled
Drive conforms to: (null):

* signifies the current active mode
```

tells me that, as I expected, DMA is already active in udma5 (ATA/100) mode. Is there a performance issue that makes you think that DMA isn't enabled on this drive?

Bob

---

### Post by darkaudit on 2005-04-10
Are you enabling an UltraDMA mode via hdparm? I had the -X70 switch set in my hdparm.conf, and caused a similar error. Once I removed it, the error went away. Turns out that mode was already enabled by the hardware, without hdparm having to do anything.

---

### Post by dukeinlondon on 2005-04-16
[QUOTE=Bob D.]Sure does. This section:

```
UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
AdvancedPM=no WriteCache=enabled
Drive conforms to: (null):

* signifies the current active mode
```

tells me that, as I expected, DMA is already active in udma5 (ATA/100) mode. Is there a performance issue that makes you think that DMA isn't enabled on this drive?

Bob[/QUOTE]

when I do large files transfers, then everything slows to a crawl, which in the past has always been resolved by running 
hdparm -d1 /dev/hda
 also, at boot, I get 
```

hda: SAMSUNG SP1604N, ATA DISK drive
hdb: MAXTOR 6L080J4, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: cannot use LBA48 DMA - PIO mode will be used for accessing sectors > 268435456
hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0:<4>hda: dma_timer_expiry: dma status == 0x61
hda: DMA timeout error
hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }

ide: failed opcode was: unknown
 p1 p2 <<4>hda: dma_timer_expiry: dma status == 0x61
hda: DMA timeout error
hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }

ide: failed opcode was: unknown
 p5<4>hda: dma_timer_expiry: dma status == 0x61
hda: DMA timeout error
hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }

ide: failed opcode was: unknown
 p6<4>hda: dma_timer_expiry: dma status == 0x61
hda: DMA timeout error
hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }

ide: failed opcode was: unknown
 p7 p8 p9 > p3
hdb: max request size: 128KiB
hdb: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100)
hdb: cache flushes supported
 /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 p6 p7 p8 p9 >
```


Thanks for the info already. :grin:

---

### Post by Dr Gonzo on 2005-04-17
Make sure your ide chipset driver is getting loaded first thing in /etc/modules.  In fact, you might also think about enabling it in /etc/mkinitrd/modules and then rebuilding your kernel initrd.  For instance, if you're using 2.6.10-5-k7, you'd do this:```
sudo mkinitrd -o /boot/initrd.img-2.6.10-5-k7 2.6.10-5-k7
```

Hope this helps.

---

### Post by dukeinlondon on 2005-04-17
[QUOTE=Dr Gonzo]Make sure your ide chipset driver is getting loaded first thing in /etc/modules.  In fact, you might also think about enabling it in /etc/mkinitrd/modules and then rebuilding your kernel initrd.  For instance, if you're using 2.6.10-5-k7, you'd do this:```
sudo mkinitrd -o /boot/initrd.img-2.6.10-5-k7 2.6.10-5-k7
```

Hope this helps.[/QUOTE]
 Thanks doc, I'll check that side of things. The strange thing though is that I have a second disk in the box and that one doesn't have any problem. But some foraging at kernel trap seems to point to a chipset problem.

---

### Post by drspin on 2005-04-21
NICE! It seems that someone else is having the same issue that I am having... same general errors. I have an ICH4 chipset (Intel)...

I have tried every version of hdparm that I can here's what I use currently and it works... sometimes...

# from /boot/grub/menu.lst
kopt=... idecore=66 ...


This is the command equivalent to my /etc/hdparm.conf
```

sudo hdparm -d1u1c3m16X69 /dev/hda
sudo hdparm -d1u1c3m16X69 /dev/hdb

```

These are for my CD drives but they don't work in the hdparm.conf as it runs before the CD drivers are loaded (this should not be the case IMO). I get /dev/hdc does not exist and the script stops (i.e. doesn't even try the next one)
```

sudo hdparm -d1u1c1X66 /dev/hdc
sudo hdparm -d1u1c1X66 /dev/hdd

```


The only drive that I ever have trouble with is /dev/hda -- and it's intermittent at best... sometimes I get the errors and other times I don't... sometimes it takes the hdparm command with no trouble and other times it throws some errors and gives up and sometimes it will hardlock and I won't be able to do anything else...

I do know that /dev/hda and /dev/hdb are starting in UDMA5 (hdparm option X69) but are not starting with dma enabled... this causes and unacceptable level of performance (i.e. I/O processor usage stays pretty high)

I am more than willing to assist all I can in solving the problem... but I'm not sure what is wrong in the first place...

Cole

---

### Post by drspin on 2005-04-22
I just had a thought -- I noticed similar errors with my CDROM drives which I recently changed out before my reinstall... the only change that I made was switching them from Cable Select to Master/Slave -> no more errors... I'm going to try this with my hard drives when I return tomorrow morning and I'll post the results.

Cole

---

### Post by drspin on 2005-04-22
Hey hey!

Alright the verdict -- I switched all of my drives to use a Master/Slave setup as opposed to a Cable Select setup... this seems to have solved my problems with cold boot. I've added the following to the file /etc/init.d/bootmisc.sh:
```

#
#       settings for disk drives
#
/sbin/hdparm -m16c3 /dev/hda
/sbin/hdparm -m16c3 /dev/hdb
/sbin/hdparm -d1u1c1X66 /dev/hdc
/sbin/hdparm -d1u1c1X66 /dev/hdd

```

```

cole@TheDesktop:~$ sudo hdparm /dev/hda

/dev/hda:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 80026361856, start = 0
cole@TheDesktop:~$ sudo hdparm /dev/hdb

/dev/hdb:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 120034123776, start = 0
cole@TheDesktop:~$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
cole@TheDesktop:~$ sudo hdparm /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
cole@TheDesktop:~$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   1380 MB in  2.01 seconds = 688.04 MB/sec
 Timing buffered disk reads:  106 MB in  3.00 seconds =  35.30 MB/sec
cole@TheDesktop:~$ sudo hdparm -tT /dev/hdb

/dev/hdb:
 Timing cached reads:   1328 MB in  2.00 seconds = 663.77 MB/sec
 Timing buffered disk reads:  166 MB in  3.04 seconds =  54.69 MB/sec

```

It seems that at boot both of my Hard Drives (hda,hdb) are using UDMA5 (hdparm -X69 /dev/hd[x])and have DMA enabled. As with most linux distros DMA is disabled on the cd drives (hdc,hdd) by default. I want them to run in UDMA2 (hdparm -X66 /dev/hd[x]) and I doubt that they run in 32bit mode w/ sync(hdparm -c3 /dev/hd[x]) -- so I just use standard 32 bit mode(hdparm -c1 /dev/hd[x]). 

All is well  \\:D/ I hope this helps someone!!

Cole

---

### Post by tomatchili on 2005-11-30
I have the same problem with dma on hda (runs on primary IDE) . On hdc and hdd (cd and dvd runs on secondary IDE) it is no problem.
I have an old Compaq 5670.

 hdparm /dev/hda

/dev/hda: 
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 234441648, start = 0

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

I have tried to change the setup in the different ways above except adding it to the .../modules file and I have neither tried the alternative where you should rebuild with mkinitrd. 
I'd like some more intructions to try these attempt. How do I find the name of the IDE chipset driver? 

If I boot without the quiet option I see that it tries to set up useDMA mthree times all of them times out.

Any more suggestetions?

Thankful for help!
Anders

---

### Post by Dr. Cox on 2006-05-06
i am just browsing through several threads and have posted something similar in another one, so don't get mad at me if you read it twice:

i happen to have similar problems. i  know that my disk is capable of running with udma5 but whatever i tried or what was tried for me with the kind help of friends refused to work. this is an error message i get:
> [4294684.020000] ide0: Speed warnings UDMA 3/4/5 is not functional

could a bios update help? i never had that problem before, though.

that is what hdparm shows about my harddisk:

> hdparm -i /dev/hda show

/dev/hda:

 Model=TOSHIBA MK6021GAS, FwRev=GA024A, SerialNo=Y3R01207T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=46
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode


my problem being: i have ich4 intel chipset, and even with loading the piix module first and changing the conf, i don't seem to be able to raise my udma level above 2.

any help is appreciated. my harddisk performance is horrid.

---

### Post by geofs on 2006-06-22
I had this problem with via chipset and solved it by adding

```
lapic acpi=off
```

to the linux boot line (in /boot/grub/menu.lst)

it also made 

```
SET: Misaligned resource pointer: dfb13922 Type 07 Len 0
```

messages disappear.  I hope that it also solves many crashes i experienced with ubuntu/kde

hope it helps

---

