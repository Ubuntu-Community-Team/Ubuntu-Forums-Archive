---
title: "SATA write speed drops after resume"
date: 2012-10-07
forum: Hardware
---

### Post by machs on 2012-10-07
I'm having a strange problem with my Precise desktop box. 

I have two hard drives, one 300GB with ubuntu and the other I use as a backup for my media, 2TB. 

During last weeks backup my rsync ran overnight and then some, not normal for an incremental backup. 

I did some googling and found out about using dd to measure drive write speeds.  Here are my results writing to starfishPrime(the 2TB) before suspending the desktop;

```
machs@electricSheep:~$ sudo time dd if=/dev/zero of=/media/starfishPrime/testfile1mb bs=16k count=16384
[sudo] password for machs: 
16384+0 records in
16384+0 records out
268435456 bytes (268 MB) copied, 1.68894 s, 159 MB/s
0.00user 0.48system 0:01.69elapsed 28%CPU (0avgtext+0avgdata 3648maxresident)k
0inputs+524288outputs (0major+285minor)pagefaults 0swaps

```

Not to shabby; roughly on par with my other drive. 

Now here are the results after a suspend and resume;

```
machs@electricSheep:~$ sudo time dd if=/dev/zero of=/media/starfishPrime/testfile1mb bs=16k count=16384
16384+0 records in
16384+0 records out
268435456 bytes (268 MB) copied, 36.5492 s, 7.3 MB/s
0.00user 0.60system 0:36.61elapsed 1%CPU (0avgtext+0avgdata 3664maxresident)k
0inputs+524288outputs (0major+286minor)pagefaults 0swaps

```

The write speed has gone down the crapper. Now to make things interesting the writespeed on sda1 stays the same after suspend and resume. 

What could be causing this?

Some other useful info.

hdparm for sdb (starfishPrime)
```

machs@electricSheep:~$ sudo hdparm -i /dev/sdb
/dev/sdb:

 Model=ST2000DL003-9VT166, FwRev=CC32, SerialNo=5YD3HSQ3
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=3907029168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

```

hdparm for sda (my OS drive) which is fine before and after. 
```

/dev/sda:

 Model=SAMSUNG HD161HJ, FwRev=JF100-22, SerialNo=S14LJ90PC63816
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312500000
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

```

---

