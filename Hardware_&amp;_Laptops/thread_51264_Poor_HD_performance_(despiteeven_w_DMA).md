---
title: "Poor HD performance (despite/even w/ DMA)"
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by Ethan on 2005-07-23
**System**

AthlonXP 2800+
Asus A7N8X Deluxe (Nforce2)
512MB DDR  RAM

HDA: WD SE Caviar; 80GB/7200 RPM/8MB cache (WD800JB-00ETA0)
HDC: Aopen DUW1608 16x DVD+-RW (~week old)

Both:

-  have a good 80-pins cable 
-  are master (and only device) on their own IDE channel


**hdparm -Tt /dev/hda**

/dev/hda:
Timing cached reads: 1464 MB in 2.00 seconds = 731.75 MB/sec
Timing buffered disk reads: 52 MB in 3.00 seconds = **17.31 MB/sec**

**(actually changing between 3MB/sec and max 18MB/sec)**

Although applications start/run fairly, prelinking helped quite a bit, the HD is performing way below what it's capable of, and below the 50-70MB/sec numbers I see around here. Even my 500MHz Athlon with a modern 160GB/7200RPM/8MB Cache disk is doing 45MB/sec (!).


**hdparm -i /dev/hda**

/dev/hda:

Model=WDC WD800JB-00ETA0, FwRev=77.07W77, SerialNo=WD-WMAHL1368725
Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=16
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio1 pio2 pio3 pio4
DMA modes: mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
AdvancedPM=no WriteCache=enabled
Drive conforms to: device does not report version:

* signifies the current active mode



And even though I can/could already set DMA=on using hdparm before adding that amd74xx line.. performance is still poor.

The amd74x module didn't help eiher...

**/etc/modules**

amd74xx
ide-core
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse


**lsmod | grep -i amd**

amd74xx 14044 1
ide_core 129548 5 ide_cd,via82cxxx,ide_generic,ide_disk,amd74xx

**hdparm -d1 /dev/hda**

/dev/hda:
setting using_dma to 1 (on)
using_dma = 1 (on)
sh-3.00# hdparm -t /dev/hda

/dev/hda:
Timing buffered disk reads: 34 MB in 3.13 seconds = 10.87 MB/sec

**Other attempts**

- I've also tried both the K7 and the 686 kernel.. no difference though.

- I've tried delaying the start of hotplug as I read somewhere on this forum, no difference.

- I've tried different IDE cables. (inc./also switched cables with 2800+ and the 500MHz I mentioned earlier which does perform just fine)


This is about everything I could find or think of as a relatively new Linux user... 

Is there anyone who might have a clue or suggestion??  :|

---

### Post by scoon on 2005-07-23
Hey there, 

2 things to check, get knoppix and try the same test and check over your bios and see if there is anything set that should not be. 

regards, 

scoon

---

### Post by Ethan on 2005-07-23
[QUOTE=scoon]Hey there, 

2 things to check, get knoppix and try the same test and check over your bios and see if there is anything set that should not be. 

regards, 

scoon[/QUOTE]

Ok, I'll do that!

BTW:

I forgot to mention that this is a dual boot system and that Win2K3 is booting in about 35 seconds. So on a hardware level this machine should be fine! :)

---

### Post by Ethan on 2005-07-23
OK, I've tried hdparm under Knoppix:

without DMA enabled (right after booting): ~2.5MB/sec
with DMA enabled*: ~ 10MB/sec
 (*could be enabled without using amd74xx module)

HDTach benchmark under Win2K3 is attached and speaks for itself...

Why oh why do I get this huge difference between *nix and Win2K3!?! :-?

---

### Post by scoon on 2005-07-23
Hey there, 

If you are using a stock kernel, my  guess is there are some conflicting modules, maybe.  The other thing to note is stock kernels are set up to be the most stable not with the greatest performance.  You should do some poking around the kernel documentation and see what you can find.  

I don't run stock kernels I patch and compile mine.  I do this because I need better bluetooth support than these kernels provide and I like to control just what options are being added. 

regards, 

scoon

---

