---
title: "Problems with reading any media with a Lite-on DVD drive"
date: 2008-07-26
forum: Hardware
---

### Post by human39 on 2008-07-26
I've been fighting with this problem for awhile, but other things took priority.

Basically, CDs and other media are not mounting on my system.  They will mount after a reboot, for a short period of time.  I've tried a bunch of different media.  Blank CD, blank DVDs, store bought DVDs, store bought CDs; they all give the same result.

Here is the information from my system:

These are the logs I'm getting:

```

[126850.685222] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[126850.685234] ata4.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[126850.685236]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
[126850.685238]          res 58/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x6 (timeout)
[126850.685241] ata4.00: status: { DRDY DRQ }
[126850.685261] ata4: soft resetting link
[126851.209494] ata4.00: configured for PIO0
[126851.209508] ata4: EH complete
[126928.831857] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[126928.831869] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[126928.831871]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[126928.831872]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[126928.831876] ata4.00: status: { DRDY }
[126928.831897] ata4: soft resetting link
[126929.356125] ata4.00: configured for PIO0
[126929.356144] ata4: EH complete

```

They just repeat.

I have a second Lite-on DVD burner that I switched it out, same results.

System information:

Linux hostname 2.6.24-20-generic #1 SMP Thu Jul 17 16:29:46 UTC 2008 i686 GNU/Linux

/etc/fstab:
/dev/scd0        /media/cdrom   udf,iso9660 user,noauto,exec 0       0

Any help would be appreciated.  I have a bunch of stuff I need to burn.

---

### Post by Pendragoon99 on 2008-07-26
> **human39 said:**
> I've been fighting with this problem for awhile, but other things took priority.

Basically, CDs and other media are not mounting on my system.  They will mount after a reboot, for a short period of time.  I've tried a bunch of different media.  Blank CD, blank DVDs, store bought DVDs, store bought CDs; they all give the same result.

Here is the information from my system:

These are the logs I'm getting:

```

[126850.685222] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[126850.685234] ata4.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[126850.685236]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
[126850.685238]          res 58/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x6 (timeout)
[126850.685241] ata4.00: status: { DRDY DRQ }
[126850.685261] ata4: soft resetting link
[126851.209494] ata4.00: configured for PIO0
[126851.209508] ata4: EH complete
[126928.831857] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[126928.831869] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[126928.831871]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[126928.831872]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[126928.831876] ata4.00: status: { DRDY }
[126928.831897] ata4: soft resetting link
[126929.356125] ata4.00: configured for PIO0
[126929.356144] ata4: EH complete

```

They just repeat.

I have a second Lite-on DVD burner that I switched it out, same results.

System information:

Linux hostname 2.6.24-20-generic #1 SMP Thu Jul 17 16:29:46 UTC 2008 i686 GNU/Linux

/etc/fstab:
/dev/scd0        /media/cdrom   udf,iso9660 user,noauto,exec 0       0

Any help would be appreciated.  I have a bunch of stuff I need to burn.

well this is more of a bump than anything , but is your burner IDE or SATA? The reason i ask is , after googling for about an hour i saw a website that said Hardy has some bug that IDE drives wont work properly. I cant get my burner to see when a blank disk is in the drive.........worked fine in windows so there nothing wrong with it internally. I thought burning an ISO in ubuntu was to be easier than windows

---

### Post by human39 on 2008-07-26
Its IDE.

Don't you think we would be hearing a lot more chatter about this if IDE drives weren't working?  I'm not sure.

Can you mount anything, Pendragoon99?  Or just blank CD's?  I can't mount anything after a period of time.

---

### Post by Pendragoon99 on 2008-07-28
> **human39 said:**
> Its IDE.

Don't you think we would be hearing a lot more chatter about this if IDE drives weren't working?  I'm not sure.

Can you mount anything, Pendragoon99?  Or just blank CD's?  I can't mount anything after a period of time.

I have been hearing alot about this and most of time the person has an IDE drive and is using Hardy. It seems to detect dvds and i can burn now............after a few restarts it magically works again. I've been using linux for about two weeks now and these things ( bugs maybe ) are a real pain in the a$$

---

### Post by human39 on 2008-07-28
My symptoms are:  After a reboot, I can read a CD/DVD and even write.  After a period of time goes by, I cannot.  It throws the "soft reset link" errors I pasted in my original post.

So, my semi-educated guess is that the drive is spinning or powering down and the system cannot wake it up?  I don't know.  

I did a fresh reboot to get the entire boot up logs and I found these:

```

[   37.363876] ata2.00: ATAPI: LITE-ON DVDRW SHM-165H6S, HS0D, max UDMA/66
[   37.363889] ata2.00: limited to UDMA/33 due to 40-wire cable
[   37.555714] ata2.00: configured for UDMA/33
...
[   37.555756] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW SHM-165H6S HS0D PQ: 0 ANSI: 5

```

output of hdparm:

```

 hdparm -i /dev/scd0

/dev/scd0:

 Model=LITE-ON DVDRW SHM-165H6S                , FwRev=HS0D    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  *sdma0 *sdma1 *sdma2 sdma? mdma0 mdma1 mdma2 
 UDMA modes: udma0 *udma1 udma2 udma3 udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

```

```
hdparm -I /dev/scd0

/dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       LITE-ON DVDRW SHM-165H6S                
	Serial Number:      
	Firmware Revision:  HS0D    
Standards:
	Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
	Supported: CD-ROM ATAPI-2 
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(cannot be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 *udma1 udma2 udma3 udma4 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	PACKET command feature set
	   *	DEVICE_RESET command
	   *	Mandatory FLUSH_CACHE
HW reset results:
	CBLID- below Vih
	Device num = 0


```

---

### Post by human39 on 2008-07-28
I should mention that the second drive I am trying and getting the same results is the Lite-On LH-20A1h,

---

### Post by kejava on 2008-07-29
human39,

sorry i missed you in the #ubuntu-us-pa channel.  i'll be back later tonight.  i'm usually there between 8 - 10 pm.  i found a bunch of info in my kernel.log and message log that closely matched the "soft resetting link" stuff you posted earlier.  i think it will be great if we can find the one thing we have in common here.  you pointed out that dvd drives models earlier.  i have a sata hard drive and pata dvd drive on this laptop:
```
ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
ata1.00: ATA-7: ST980811AS, 3.CDD, max UDMA/133
ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
ata1.00: configured for UDMA/133
ata2.00: ATAPI: SONY CD-RW/DVD-ROM CRX880A, KD09, max UDMA/33
```

but i think the biggest culprit may be the IDE controller.  my controller supports both pata and sata drives:
```
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
```

oh yeah, i just noticed this when i switched from feisty to hardy a few weeks back.  it's very intermittent.

---

### Post by human39 on 2008-07-29
kejava, 

As I said previously.  All my drives (include two internal HD are IDE).

You mentioned in IRC that you are having freeze issues, I am not.

```
06:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b0)
```

I'm not sure when this started happen.  I've been reading that most drive are now using the SATA driver (PATA or not).  I've been out of the loop for awhile.

Hard drives are just fine.  Are you looking for anything specific out of my logs?

---

### Post by mc4man on 2008-07-29
>   37.363876] ata2.00: ATAPI: LITE-ON DVDRW SHM-165H6S, HS0D, max UDMA/66
[   37.363889] ata2.00: limited to UDMA/33 due to 40-wire cable
[   37.555714] ata2.00: configured for UDMA/33

You should replace the current 40 wire ide cable with an 80 wire, will cause you continual issues the way your setup now.
An 80 wire is smooth looking, hard to see the individual wires unlike the 40.

>  UDMA modes: udma0 *udma1 udma2 udma3 udma4 
udma1 is not what you want with that drive  (cable related)

---

### Post by human39 on 2008-07-29
> You should replace the current 40 wire ide cable with an 80 wire, will cause you continual issues the way your setup now.
An 80 wire is smooth looking, hard to see the individual wires unlike the 40.


Thanks for your reply mc4man, but it is the 80 pin cable.  I even switched it out for good measure. 

```

[   28.341690] ata2.01: ATAPI: LITE-ON DVDRW LH-20A1H, LL0A, max UDMA/66
[   28.341702] ata2.01: limited to UDMA/33 due to 40-wire cable
[   28.529528] ata2.01: configured for UDMA/33

```

Same issues.

---

### Post by kejava on 2008-07-29
Here's a paste bin from one of my /var/log/message files.  As you'll see, my messages are fairly similar.  Mine sometimes can't even read the model number.
[http://pastebin.org/58334](http://pastebin.org/58334)

It hasn't come back for about 3 days now.  I've been trying to keep track of what i'm doing for when it surfaces again.  Mine seemed to only happen when i tried to watch DVDs using totem.  I powered down, pulled the DVD drive from the laptop, and then reseated it.  Problem went away.  Doesn't mean that's the solution though.  I think i just got lucky - momentarily.

---

### Post by mc4man on 2008-07-29
> but it is the 80 pin cable. I even switched it out for good measure. 
That is odd but apparently true. I just tonight had switched out a plextor 716a for a new liteon and can see the same thing. No performance issues as of yet, the read/transfer rate was pretty good. It's only slightly slower than the plextor and on par with my Benq 1640 (udma2).

The plextor was configured for udma/66, and showed being set to udma4 in hdparm. The liteon is dma4 capable, but is set here to udma2, and the same syslog message about 40 wire, setting to udma/33 you see. 
Has got me curious as to what's up, 

```
ATAPI CD-ROM, with removable media
	Model Number:       ATAPI   DVD A  DH20A4P                  
	Serial Number:      
	Firmware Revision:  9P59    
Standards:
	Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
	Supported: CD-ROM ATAPI-2 
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(cannot be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	PACKET command feature set
	   *	DEVICE_RESET command
	   *	Mandatory FLUSH_CACHE
HW reset results:
	CBLID- below Vih
	Device num = 0

```

Overall the udma4 vs udma2 thing I don't think is a big factor.If you were also getting something like this, then it would be.
> Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0

The exact same thing happens in 7.10 also, udma2, 40 wire ect., though a quick trip to Xp device manager shows the drive being set to udma4. Seems to be a quirk of lite-on and linux, reasonably harmless, at least here atm.

i do think the udma1 you're showing is something to look at, where is the drive connected? Mastered on secondary ide would be best  (end connector)

---

### Post by human39 on 2008-07-30
> Mastered on secondary ide would be best (end connector)

This is correct.  The jumper is set to Master and its the only thing on the secondary IDE channel.

I've tried to disable the power management settings with hdparm and blktool, which is supposed to work better with drives using the sata drivers and it gives me an error.  Do you think this is barking up the wrong tree?

---

### Post by mc4man on 2008-07-30
> Do you think this is barking up the wrong tree Don't know.  While hdparm is only good for reporting in 8.04, blktool can make some changes so I'd be careful there. If you run just > blktool from the terminal anything listed as 'any' can be used. I'd just use it for reporting ie. don't have an action or setting after the arguement.

Just an observation
> [126850.685222] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[126850.685234] ata4.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[126850.685236]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
[126850.685238]          res 58/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x6 (timeout)
[126850.685241] ata4.00: status: { DRDY DRQ }
[126850.685261] ata4: soft resetting link
[126851.209494] ata4.00: configured for PIO0
In one post your dvd drive is ata2.00, in another it's ata2.01 but not ata4.00. (normally ata4.00 would be a hdd when you have sata hdd(s)
Also note ata4.00 is being set to pio mode0

What does this show
```
 grep 'ata' /var/log/syslog 
```

What might be interesting to see is this (run in maximized terminal for readability)
 ```
cat /etc/udev/rules.d/70-persistent-cd.rules
```  
and also this
```
sudo lshw -C disk
```

I get the feeling if you did a fresh install of hardy all would be well.
You could also boot to a live cd of hardy and run some of the various commands to cross compare against what is being shown in your present install

---

### Post by human39 on 2008-07-30
> I get the feeling if you did a fresh install of hardy all would be well.

I was afraid of this.  I did do the Fiesty -> Hardy Upgrade, not a fresh install.

> In one post your dvd drive is ata2.00, in another it's ata2.01 but not ata4.00. 

I've been swapping out drives testing things and such, my copies might of been crossed.  Good point, its not consistent, I'll paste a new one later when I get home, along with the other info you requested.

Thanks again.

---

### Post by mc4man on 2008-07-30
the ata2.00 and ata2.01 thing won't be an issue - you'll see what i mean when you look in ....rules.
Will be interested to see what everything shows.

The idea behind having a live cd of hardy is it will allow you to see what a 'proper' setup of hardy is vs. what you've got now

cya later

---

### Post by human39 on 2008-07-30
grep 'ata' /var/log/syslog

A bunch of these:
```

Jul 30 16:10:43 hostname kernel: [71062.832752] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jul 30 16:10:43 hostname kernel: [71062.832764] ata2.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jul 30 16:10:43 hostname kernel: [71062.832770] ata2.01: status: { DRDY }
Jul 30 16:10:43 hostname kernel: [71062.832788] ata2: soft resetting link
Jul 30 16:10:44 hostname kernel: [71063.544877] ata2.01: configured for UDMA/25
Jul 30 16:10:44 hostname kernel: [71063.544892] ata2: EH complete

```

cat /etc/udev/rules.d/70-persistent-cd.rules

```

# LITE-ON_DVDRW_LH-20A1H (pci-0000:00:0f.1-ide-1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DVDRW_LH-20A1H (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
# DVDRW_SHM-165H6S (pci-0000:00:0f.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"
# DVDRW_LH-20A1H (pci-0000:00:0f.0-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:1:0", SYMLINK+="cdrom3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:1:0", SYMLINK+="cdrw3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:1:0", SYMLINK+="dvd3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:1:0", SYMLINK+="dvdrw3", ENV{GENERATED}="1"
```

sudo lshw -C disk

```

  *-disk:0                
       description: ATA Disk
       product: MAXTOR STM332062
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5QF1Y8BD
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00060334
  *-disk:1
       description: ATA Disk
       product: ST380013A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 3.54
       serial: 3JT3A7AL
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=116f49d9
  *-cdrom
       description: DVD-RAM writer
       product: DVDRW LH-20A1H
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@1:0.1.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: LL0A
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/scd0
  *-disk:0
       description: SCSI Disk
       product: ImageMate 6 in 1
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 0.0>
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:1
       description: SCSI Disk
       product: ImageMate 6 in 1
       vendor: SanDisk
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdd
       version: 0.0>
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:2
       description: SCSI Disk
       product: ImageMate 6 in 1
       vendor: SanDisk
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sde
       version: 0.0>
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
  *-disk:3
       description: SCSI Disk
       product: ImageMate 6 in 1
       vendor: SanDisk
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sdf
       version: 0.0>
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdf
```

---

### Post by mc4man on 2008-07-30
Lets try something run  (copy and paste below so you don't inadvertently mistype and open an empty file)
```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
``` and delete all the entries, save and reboot. I'm not familar with the 6 in 1, _if it's possible disconnect before rebooting._(probably not important but ..)
leave your ...rules looking like this

> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


then after reboot run the cat .... rules and see what the entry looks like and ck your logs for the 'soft reset' (I tend to think it will reappear)

i'm not to sure this will help but won't hurt to try and would eliminate 1 'outside possibility' for your issues plus should give your drive proper /dev/links for your install

---

### Post by human39 on 2008-07-30
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVDRW_LH-20A1H (pci-0000:00:0f.0-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
```


The 6 in 1 is my USB memory card reader, I unplugged it.

Here are some relevant entries (I hope) 

```
[   23.565674] ata4.01: ATAPI: LITE-ON DVDRW LH-20A1H, LL0A, max UDMA/66
[   23.565686] ata4.01: limited to UDMA/33 due to 40-wire cable

[   23.758358] scsi 3:0:1:0: CD-ROM            LITE-ON  DVDRW LH-20A1H   LL0A PQ: 0 ANSI: 5


[   23.978858] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.978863] Uniform CD-ROM driver Revision: 3.20
[   23.978910] sr 3:0:1:0: Attached scsi CD-ROM sr0
```

Actually, here is my entire dmesg from the recent boot.

[http://pastebin.ca/1087743](http://pastebin.ca/1087743)

---

### Post by mc4man on 2008-07-30
your ...rules is good now.
Do you think there is there is any difference/ does hdparm -I show udma2 or 1?
your certainly not alone with that soft reset, most of the posts concerning cd/dvd drives mention liteon.

[http://www.google.co.uk/custom?q=soft+resetting+link+in+ubuntu&sa=Search&client=pub-2070091971271392&forid=1&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A1](http://www.google.co.uk/custom?q=soft+resetting+link+in+ubuntu&sa=Search&client=pub-2070091971271392&forid=1&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A1)

While I take sudo hdparm -tT /dev/scd0 (or scd1 ect.) with a grain of salt on 2 boxes (4 dvd drives total) the liteon is the worst performer.(by far ). A real world test here (ripping dvd) it performed good - 7.7Gb in 11 min.

There's no way your hdd drives are on a 40 wire?

There are some kernel parameters that some people have had limited success with

edit : don't know enough to say about your dmesg though the info on your drives (hdd and dvd) appears ok. Comparing a very similar setup on a test box from fresh install only shows minor diffs. (2 hdd on primary ide, faster drive mastered, 2 dvd drives on secondary)
```
ul 30 12:44:25 doug-desktop kernel: [   26.430728] ata1.00: ATA-5: MAXTOR 6L040J2, A93.0500, max UDMA/133
Jul 30 12:44:25 doug-desktop kernel: [   26.430734] ata1.00: 78177792 sectors, multi 8: LBA 
Jul 30 12:44:25 doug-desktop kernel: [   26.431692] ata1.01: ATA-5: WDC WD400BB-75AUA1, 18.20D18, max UDMA/100
Jul 30 12:44:25 doug-desktop kernel: [   26.431698] ata1.01: 78165360 sectors, multi 8: LBA 
Jul 30 12:44:25 doug-desktop kernel: [   26.446591] ata1.00: configured for UDMA/100
Jul 30 12:44:25 doug-desktop kernel: [   26.463298] ata1.01: configured for UDMA/100
Jul 30 12:44:25 doug-desktop kernel: [   26.946124] ata2.00: ATAPI: PLEXTOR DVDR   PX-712A, 1.08, max UDMA/33
Jul 30 12:44:25 doug-desktop kernel: [   26.946157] ata2.01: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
Jul 30 12:44:25 doug-desktop kernel: [   27.109930] ata2.00: configured for UDMA/33
Jul 30 12:44:25 doug-desktop kernel: [   27.281814] ata2.01: configured for UDMA/33
Jul 30 12:44:25 doug-desktop kernel: [   27.281968] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR 6L040J2   A93. PQ: 0 ANSI: 5
Jul 30 12:44:25 doug-desktop kernel: [   27.282488] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400BB-75AU 18.2 PQ: 0 ANSI: 5
Jul 30 12:44:25 doug-desktop kernel: [   27.283391] scsi 1:0:0:0: CD-ROM            PLEXTOR  DVDR   PX-712A   1.08 PQ: 0 ANSI: 5
Jul 30 12:44:25 doug-desktop kernel: [   27.286994] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
```

What i'm presuming is that on an upgrade all your atax.xx get 'bumped up' so that's why you show ata3.00 for one hdd, ata3.01 for the other, ata4.01 for your dvd drive vs. mine which start at ata1.00 and progress up logically

---

### Post by slowth5 on 2008-07-30
I'm experiencing the same problem with my Lite-on drive.  Problem does not exist in Gutsy, and a fresh install of Hardy did not rectify the issue. Fedora 9 exhibited same aberrant behavior.

---

### Post by human39 on 2008-07-30
I let things go for a few hours and try putting a CD in a drive and it auto-mounted it without a problem.  This is a definite improvement.

I'm watching a DVD right now!

How do these look?  What are the ideal DMA settings? 

```
 hdparm -i /dev/scd0

/dev/scd0:

 Model=LITE-ON DVDRW LH-20A1H                  , FwRev=LL0A    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  *sdma0 *sdma1 *sdma2 sdma? mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode
```


```
/dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       LITE-ON DVDRW LH-20A1H                  
	Serial Number:      
	Firmware Revision:  LL0A    
Standards:
	Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
	Supported: CD-ROM ATAPI-2 
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(cannot be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	PACKET command feature set
	   *	DEVICE_RESET command
	   *	Mandatory FLUSH_CACHE
HW reset results:
	CBLID- below Vih
	Device num = 0

```

```
sudo hdparm -tT /dev/scd0

/dev/scd0:
 Timing cached reads:     2 MB in  2.46 seconds = 831.41 kB/sec
 Timing buffered disk reads:    6 MB in  3.49 seconds =   1.72 MB/sec
```

---

### Post by mc4man on 2008-07-30
> What are the ideal DMA settings?  Udma2 is apparently the best these liteon drives can do in linux. Many (most ?)  dvd drives are set to udma2 so performance for reading and writing isn't an issue at that setting.
It is somewhat disappointing they aren't configured @ udma/66 (udma4) but I can't see any user solution to that. Overall the liteon I installed yesterday seems fine in use.

Edit: in other words your hdparm looks like mine now, so hopefully things should work well.

---

### Post by mc4man on 2008-07-31
forgot to add 
Your  'Timing buffered disk reads' is low  (here's mine for the the liteon
 > Timing cached reads:   1304 MB in  2.00 seconds = 651.91 MB/sec
 Timing buffered disk reads:   10 MB in  3.01 seconds =   3.32 MB/sec

I'd consider this low also compared to _all_ my other drives, but as I mentioned before i would balance those results with what you see in the 'real world' so to speak. 
Mine is performing as an above average drive. (as i mentioned a read/transfer of 7.7Gb. in 11 min., no playback issues, ect.)
There certainly is an 'issue' between liteon and linux

---

### Post by slowth5 on 2008-07-31
I'm not sure what you did to correct the issue.  Would you please explain?

---

### Post by human39 on 2008-07-31
slowth5, unfortunately; its not fixed.  I tried mounting a CD again this morning is the problem is still there.

So, at this point, I figure my options are: doing a fresh install of Hardy or buying a CD/DVD burning that is reported to work

I'm taking a suggestions for DVD/CD drives.  I prefer it to write all formats (+/-, r/rw).  LightScribe, but thats not mandatory

Thanks again everybody.

---

### Post by slowth5 on 2008-07-31
Thank you for responding. A fresh install of Hardy did not correct the issue, but hopefully it will work for you. Since this also occurred with a fresh Fedora 9 install, I'm led to believe this is a kernel or Gnome problem.  Either way, there seems to be no turning back, so I guess I'll purchase a new drive as well.

---

### Post by mc4man on 2008-08-01
> A fresh install of Hardy did not correct the issue,
Assuming nothings wrong with the drive you have and it's an ide drive you may want to try some of the various kernel parameters first before buying a new drive. A little research shows it many different models of drives may have issues. 
Try searching all-generic-ide or try the one in this post that was successful
[http://ubuntuforums.org/showthread.php?t=863412](http://ubuntuforums.org/showthread.php?t=863412)

If none of those maybe try searching based more on your main hardware combo (mobo, chipset, cpu,) for instance
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639)

The other possibility is your drive does require an 80 wire cable and you have a 40. I'd think you'd see this or similar somewhere in a log.
> Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0 


The whole 'limited to UDMA/33 due to 40-wire cable' thing is a non factor, some drives that are udma/66 capable can be set to udma4, some can't. Looked and can see that happening with this liteon as far back as feisty. At best the liteon shows an 8% performance increase at umda4 in xp, no big deal.

---

### Post by slowth5 on 2008-08-01
human39,

I tried this suggestion from ArcherB and it seems to have solved the problem with no ill effects. I will update if I notice any further issues.  Thanks for pointing me in the right direction mc4man!


> **ArcherB said:**
> I had the same problem and was beating my head against the desk trying to figure it out.  Finally, I found a post that suggested adding noapic to the end of the kernel line in your /boot/grub/menu.lst file.  The post suggested a few other items that didn't work (made my mouse disappear), but just the noapic seemed to fix the problem for me.

However, before changing your menu.lst file, try typing it in at boot just to make sure it works out OK before making the change permenent.

---

### Post by human39 on 2008-08-01
Again, thanks to everybody who has responded.

slowth5:  Could you post a link to the thread that you got that answer in?  I would like to look at. 

mc4man:  I'm certain that the IDE connector is 80 pin.  Granted, my hardware skills are a bit rusty.  I am humble so, hell, I'll even take a picture if that would help for clarity sake (informational and possible bugs too). 

I'll grep through the log for the error.  Thanks.

I'm going to get specs of my motherboard and BIOS and post them.  I also have not checked for any bios upgrades lately, I'll do that as well.

A co-worker is (hopefully) going to let me borrow a CD/DVD burner.  I do photography as a hobby and I need the pictures backed up; Like now :-).  I told him that I didn't care if it was IDE or SATA, just "Not Lite-on".

---

### Post by mc4man on 2008-08-01
>  Could you post a link to the thread that you got that answer in? I would like to look at.

[http://ubuntuforums.org/showthread.php?t=863412](http://ubuntuforums.org/showthread.php?t=863412)

---

### Post by human39 on 2008-08-01
Another thought:

Do you think this is an IDE (PATA) issue?  Like if I goto a SATA optical drive with the kernel drivers things would, in general, be better?

Also, my co-worker came through with the burner.  IDE Samsung.  I'll post my findings.

---

### Post by human39 on 2008-08-02
I just installed the borrowed CD/DVD burner and went from there.

In dmesg, its coming up as:
```

[   30.922894] ata2.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB02, max UDMA/33
[   31.094745] ata2.00: configured for UDMA/33
 ...
[   31.095748] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB02 PQ: 0 ANSI: 5

```

Note:  There is no error about not having a 80 pin PATA cable.

```

hdparm -i /dev/scd0

/dev/scd0:

 Model=TSSTcorpCD/DVDW SH-S182D                , FwRev=SB02    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode

hdparm -i /dev/scd0

/dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       TSSTcorpCD/DVDW SH-S182D                
	Serial Number:      
	Firmware Revision:  SB02    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=227ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
HW reset results:
	CBLID- below Vih
	Device num = 0

lshw -C disk

  *-cdrom
       description: DVD-RAM writer
       product: CD/DVDW SH-S182D
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open

```

UGH, I'm getting the SAME error.  3 Drive.  All IDE, 2 different brands.

```

[ 1402.097628] ata2.00: limiting speed to UDMA/25:PIO4
[ 1402.097636] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1402.097646] ata2.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[ 1402.097648]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[ 1402.097649]          res 58/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x6 (timeout)
[ 1402.097652] ata2.00: status: { DRDY DRQ }
[ 1402.097670] ata2: soft resetting link
[ 1402.589772] ata2.00: configured for UDMA/25
[ 1402.589791] ata2: EH complete

```

Also.. getting these...
```

[ 1256.132022] sr 1:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[ 1256.132031] sr 1:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present - tray closed
[ 1256.132039] end_request: I/O error, dev sr0, sector 256
[ 1256.132041] printk: 54 messages suppressed.
[ 1256.132044] Buffer I/O error on device sr0, logical block 64
[ 1256.132049] Buffer I/O error on device sr0, logical block 65
[ 1256.132053] Buffer I/O error on device sr0, logical block 66
[ 1256.132058] Buffer I/O error on device sr0, logical block 67

```

I'm going to try slowth5 suggestion and add that boot param.  I'll also drop into the bios and grab info there.

---

### Post by human39 on 2008-08-04
Adding the 'noapic' kernel param has fixed my issue.  I'm going to add more information later to this post for future reference.  Such as; My MB and bios information.

I might purchase a SATA drive as well to see if that ultimately just makes this work.

---

### Post by ArcherB on 2009-05-15
> **slowth5 said:**
> human39,

I tried this suggestion from ArcherB and it seems to have solved the problem with no ill effects. I will update if I notice any further issues.  Thanks for pointing me in the right direction mc4man!

How sad!  I've been experiencing this issue again and completely forgot how I fixed it the first time.  Thanx Human for reminding me.

It's sad because I've been going without a CD/DVD ROM/RW for at least six months when I did a clean install of the latest LinuxMint.  The maintainer of Mint asked me to no longer use Mint (well, not directly... long story) so I did a clean install of Ubuntu and it didn't fix the problem.  I've been relying on my 64-bit Ubuntu box for all my DVD needs.  I don't know if it has the NOAPIC switch in there or not or if the root cause is something else entirely (other system is a Core2Duo, 64-bit box while this one is an AMD running the 32-bit version).

Either way, how soon we forget.  Thanx for the reminder, Human.

Just in case I forget again, here are the log files I was searching from that didn't lead me back to this bug:

```
May 14 20:45:53 Opteron kernel: [ 3160.989087] ata7: soft resetting link
May 14 20:45:53 Opteron kernel: [ 3161.321320] ata7.00: configured for UDMA/66
May 14 20:45:54 Opteron kernel: [ 3161.337312] ata7.01: configured for UDMA/33
May 14 20:45:59 Opteron kernel: [ 3166.337038] ata7.00: qc timeout (cmd 0xa0)
May 14 20:45:59 Opteron kernel: [ 3166.337046] ata7.00: TEST_UNIT_READY failed (err_mask=0x4)
May 14 20:45:59 Opteron kernel: [ 3166.337092] ata7: soft resetting link
May 14 20:45:59 Opteron kernel: [ 3166.669359] ata7.00: configured for UDMA/66
May 14 20:45:59 Opteron kernel: [ 3166.685318] ata7.01: configured for UDMA/33
May 14 20:46:04 Opteron kernel: [ 3171.685037] ata7.00: qc timeout (cmd 0xa0)
May 14 20:46:04 Opteron kernel: [ 3171.685049] ata7.00: TEST_UNIT_READY failed (err_mask=0x4)
May 14 20:46:04 Opteron kernel: [ 3171.685054] ata7.00: limiting speed to UDMA/66:PIO3
May 14 20:46:04 Opteron kernel: [ 3171.685075] ata7: soft resetting link
May 14 20:46:04 Opteron kernel: [ 3172.017440] ata7.00: configured for UDMA/66
May 14 20:46:04 Opteron kernel: [ 3172.033293] ata7.01: configured for UDMA/33
May 14 20:46:09 Opteron kernel: [ 3177.033051] ata7.00: qc timeout (cmd 0xa0)
May 14 20:46:09 Opteron kernel: [ 3177.033059] ata7.00: TEST_UNIT_READY failed (err_mask=0x4)
May 14 20:46:09 Opteron kernel: [ 3177.033062] ata7.00: disabled
May 14 20:46:09 Opteron kernel: [ 3177.033072] ata7.01: TEST_UNIT_READY failed (err_mask=0x40)
May 14 20:46:09 Opteron kernel: [ 3177.033092] ata7: soft resetting link
May 14 20:46:10 Opteron kernel: [ 3177.325292] ata7.01: configured for UDMA/33
May 14 20:46:15 Opteron kernel: [ 3182.325035] ata7.01: qc timeout (cmd 0xa0)
May 14 20:46:15 Opteron kernel: [ 3182.325055] ata7.01: TEST_UNIT_READY failed (err_mask=0x4)
May 14 20:46:15 Opteron kernel: [ 3182.325059] ata7.01: limiting speed to UDMA/33:PIO3
May 14 20:46:15 Opteron kernel: [ 3182.325080] ata7: soft resetting link
May 14 20:46:15 Opteron kernel: [ 3182.617343] ata7.01: configured for UDMA/33
May 14 20:46:20 Opteron kernel: [ 3187.617041] ata7.01: qc timeout (cmd 0xa0)
May 14 20:46:20 Opteron kernel: [ 3187.617067] ata7.01: TEST_UNIT_READY failed (err_mask=0x4)
May 14 20:46:20 Opteron kernel: [ 3187.617074] ata7.01: disabled
May 14 20:46:20 Opteron kernel: [ 3187.617110] ata7: soft resetting link
May 14 20:46:20 Opteron kernel: [ 3187.885143] ata7: EH complete
```

---

### Post by mickey57 on 2009-06-01
[COLOR="DarkRed"][SIZE="4"]Is there any fix for this problem?
....Every thing on my system would be just fine if I could use my cd/dvd roms ;) and keep that damn pulse audio out ;).[/SIZE][/COLOR]

---

