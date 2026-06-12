---
title: "pathetically slow SATA (Sil 3124 controller)"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by sdac1_0 on 2007-06-03
Hi,  my WD 1200JS SATA HD (connected through Sil 3124) is running very slow on linux (fiesty).

```

hdparm -tT /dev/sda    
________________

/dev/sda:
 Timing cached reads:   140 MB in  2.03 seconds =  69.00 MB/sec
 Timing buffered disk reads:  102 MB in  3.18 seconds =  32.09 MB/sec

```


Tried another linux distro and also got very poor results,  the system is slow and video playback somewhat choppy.

I read online about these issue and it seems many people are experiencing such problems with SATA drivers but I haven't 
been able to find a solution.

[http://ubuntuforums.org/showthread.php?t=400356](http://ubuntuforums.org/showthread.php?t=400356)
[http://ubuntuforums.org/showthread.php?t=253252](http://ubuntuforums.org/showthread.php?t=253252)


Please point me in the right direction to solve this issue as my system is not very usable and I don't want to try putting Windows on this :(
I'm relatively new to Linux and have not been able to make sense of advanced discussions I've found on the net.
[COLOR="DeepSkyBlue"]
Should I update the BIOS of the Sil3124 from the website ?  If so should i install a non-RAID BIOS since i only have 1 HD ?
Should I update the kernel (Linux 2.6.20-16-generic) with some patch ?
Should I update the Sil3124 driver on fiesty by searching for a newer driver online ?
[/COLOR]


Let me know if any more info is needed.  thanks 

||||||||||||||||||||||||||||||||||||||||||||
        more info:
||||||||||||||||||||||||||||||||||||||||||||

```

lshw -C disk
__________

description: SCSI Disk
       product: WDC WD1200JS-00N
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 10.0
       serial: WD-........
       size: 111GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5

```

```

sudo hdparm -i /dev/sda
____________________

/dev/sda:

 Model=WDC WD1200JS-00NCB1                     , FwRev=10.02E02, SerialNo=     WD-........
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

```

---

### Post by StonedSidney on 2007-07-10
Same here as posted in  [http://ubuntuforums.org/showthread.php?t=447474&highlight=slow+sata&page=3]("http://ubuntuforums.org/showthread.php?t=447474&highlight=slow+sata&page=3")

Note that I have the same SIL 3124 controller as you, but I am also getting the same problem with the ATI onboard SATA controller, so IMHO it's not the controller's problem.

I am running 64bit Dapper but there are a quite a few posters using Feisty, so I'm not sure that an upgrade would improve things.

Also it seems that the output of HDParm isn't indicative of real world performance. 

When you do (say) a file copy do you see a high WA% in TOP like I do?

My drives are Seagate 320GB SATAII with the jumper set to SATAII, not the factory default of SATAI (stupid default). They also have 16mb cache, so I expected a much score for cached reads.

When I try: sudo hdparm -i /dev/sda I get: HDIO_GET_IDENTITY failed: Inappropriate ioctl for device

I would try using a live CD but Ubuntu won't burn CD's for me - another damn annoyance. Hmmm maybe related? Although DVD iso burning works fine on the same drive.

At least my RAID5 speads up reading my music and movies.

---

