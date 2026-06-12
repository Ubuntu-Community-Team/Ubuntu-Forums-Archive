---
title: "Hard disk only detected as udma33!?"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by reech on 2006-06-10
Hi - My hdd is only detected as udma33 - it is capable of  udma100 and runs as such under XP. When I attempt to set the udma mode via hdparm it reports that it has been done but sticks  to udma33.
dmesg:
```
[4294672.227000]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:pio
[4294672.492000] hda: IC25N030ATCS04-0, ATA DISK drive
[4294673.138000] hda: max request size: 128KiB
[4294673.138000] hda: 58605120 sectors (30005 MB) w/1768KiB Cache, CHS=58140/16/63, UDMA(33)
[4294673.139000] hda: cache flushes not supported
[4294673.139000]  hda: hda1 hda2 < hda5 >
[4294703.966000] Adding 1036152k swap on /dev/hda5.  Priority:-1 extents:1 across:1036152k
[4294704.044000] EXT3 FS on hda1, internal journal
```

hdparm -i:
```
/dev/hda:

 Model=IC25N030ATCS04-0, FwRev=CA3OA71A, SerialNo=CSH309DJCWLZ8B
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=1768kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=58605120
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 3:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode
```

Please help - my hdd speeds are terrible!

---

### Post by stanz on 2006-06-25
Hi.. I'm trying to work things out also...but- if it helps..
[Linuxdevcenter]("http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html") gives some details.
[another off-site]("http://www.linuxnetmag.com/en/issue7/m7hdparm1.html") help.
I'm searching round for a post- that describes making your own script,
placing it in /etc.init.d/, and running it for sure in /rcS.d.
There's so much to check on, and to make sure~ works with your hd.
your on 'udma2', where mine is '5'...now don't ask me why.. :)
Search- Read- Google- Read more...some more....

---

### Post by reech on 2006-06-26
Thanks Stanz - I've googled this to death, done irc, no-one seems to know - when I set the speed with :

```

hdparm -X69 /dev/hda

```

for instance it reports that the bus speed has been changed to udma mode 5 - but there are absolutely no performance improvements.

Aaargh.

---

