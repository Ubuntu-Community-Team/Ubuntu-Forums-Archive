---
title: "Extreme random slowness (almost freezing) during use - HDD problem?"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by db0 on 2007-11-15
Hello all, I've been using Gutsy for a while now with no large problems but now I have run into a roadblock (especially at a time when it shouldn't happen but that's another story)

What happened is that I decided to install Vista in VirtualBox in order to train for a mandatory test in my company. (the virtual hdd was on my home dir) As soon as I started the installation, the system experienced extreme slowness, to the point where the music from Amarok stopped playing and nothing would respond. At some points the Vista installation would move an inch and some programs would start responding for a few seconds but stop again. The whole system was unusable. I couldn't even manage to stop the installation so I just went for a cold reboot. During the boot, I noticed an error message but I could not note it down, however after the boot, the system become just horrible and it stays that way right now:

[LIST]
[*]Programs will just stop responding without apparent reason. When this happens, only the active program might stop but most often, the whole system will stop responding and occasionally mouse and keyboard as well. If I wait a few minutes, it will recover
[*]If I try to do any writing on the home directory (and I'm guessing the whole HDD that hosts my main system). The system becomes totally unresponsive. Quite like the previous symptom, but the effect will not stop until the write job ends or I cancel it (or at least it seems that way to me). If this keeps on for long enough, as before, even music will stop (when the current playing song ends).
[*]On a hunch, I went to the terminal (alt-f1) and tried to log in from there. The following was what came up (and still does when the system starts freezing)
```
[71478.621121] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[71478.621258] ata1.00: cmd ca/00:78:18:af:9c/00:00:00:00:00/e6 tag 0 cdb 0x0 data 61440 out
```
[*]I tried running smartcrl on the disk but both short and long tests completed without error.
[*]I tried running bonnie++ and after the initial lock up as the program started writing (at which point I went to work for 8 hous) it finished but I could not see any errors (I can provide output if anyone wishes as I can't make any sense of it)
[/LIST]

So can anyone help me find out what is going on? I am afraid my HDD is b0rking but I can't be sure. Could be the RAM but a very quick memmtest did not return errors (first 3 tests at least. Didn't have time for more)
If the HDD is dying, I can try to change it but perhaps there is just some monitoring I can disable to stop this slowdown until I have time to replace? I honestly don't know.

Some more info
```

$hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0

$hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD2500KS-00MJB0                     , FwRev=02.01C03, SerialNo=     WD-WCANK7909250
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
```

Help?

---

### Post by db0 on 2007-11-16
Looking around, I've found some similar stuff

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603)

Not certain how similar it is. For now I'm downloading Fedora just to see if this will keep happening there as well

---

### Post by db0 on 2007-11-17
Hmmm, I played around with my SATA cables and the system seems stable once again now...Judging by the bugs I guess it will return at some point though :-/

---

