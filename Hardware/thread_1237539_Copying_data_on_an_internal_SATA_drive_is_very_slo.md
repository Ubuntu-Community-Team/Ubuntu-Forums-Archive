---
title: "Copying data on an internal SATA drive is very slow"
date: 2009-08-11
forum: Hardware
---

### Post by LingaringBell on 2009-08-11
I am running Ubuntu 9 desktop 64 bit on a machine with two internal drives (one has Ubuntu, the other is just data).  On both drives it takes a very long time to copy files, both form one drive to another and just dublicating a file on the same drive.  This is the hdparm output for the data drive:

sysadmin@sysadmin-desktop:~$ sudo hdparm -i /dev/sdb1

/dev/sdb1:

 Model=WDC WD2500JD-40HBC0                     , FwRev=21.02J21, SerialNo=     WD-WCAL75348674
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode


It looks to me like it is using the proper udma mode, but I'm still new to this.  If I run a few tests using hdparm, sometimes I get:

sysadmin@sysadmin-desktop:~$ sudo hdparm -tT /dev/sdb1

/dev/sdb1:
 Timing cached reads:   6400 MB in  2.00 seconds = 3201.50 MB/sec
 Timing buffered disk reads:  172 MB in  3.01 seconds =  57.05 MB/sec

and sometimes I get:

/dev/sdb1:
 Timing cached reads:   3612 MB in  2.00 seconds = 1806.21 MB/sec
 Timing buffered disk reads:   44 MB in  3.19 seconds =  13.80 MB/sec

Is there something I need to do more consistant speeds?  Thanks for the help.
-Bell

---

### Post by realzippy on 2009-08-11
Your $ sudo hdparm -i /dev/sdb1 output is ok.UltraDMA6 is running.

sudo hdparm -tT /dev/sdb1 output seems to be slow,mine is:
/dev/sda1:
 Timing cached reads:   12718 MB in  2.00 seconds = 6367.24 MB/sec
 Timing buffered disk reads:  188 MB in  2.24 seconds =  84.00 MB/sec


..but you can copy a large file,e.g. a dvd.iso from your dataHD to the other
and see how much time it takes...then you have a REAL benchmark.It should
be pretty fast cause one disc reads and the other writes.More than 100 MB/sec...

---

### Post by realzippy on 2009-08-11
Sorry,your output is **not** ok (had to look twice):
Model=WDC WD2500JD-40HBC0 , FwRev=21.02J21, SerialNo= WD-WCAL75348674
Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, [COLOR="Red"]MultSect=?0?[/COLOR]
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio1 pio2 pio3 pio4
DMA modes: mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
AdvancedPM=no WriteCache=enabled
Drive conforms to: Unspecified: ATA/ATAPI-1,2,3,4,5,6

As you can see,your hd can do blockmode (MaxMultSect=16),but it is not used (MultSect=?0?)
You can enable it:

**sudo hdparm -m16 /dev/sdb**   (not sdb1)

do it also for your second hd (sda?)

---

### Post by LingaringBell on 2009-08-11
Thanks for the input realzippy, I did as you suggested and got an error:

/dev/sdb:
 setting multcount to 16
 HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
 HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device

Any ideas?

---

### Post by realzippy on 2009-08-11
Again,copy a large file and you will see if there is something wrong.
Run

**sudo hdparm -tT /dev/sda**  (sdb)

a few more times without anything running in the backround,and see if it continues to slowdown to 13 MB/s...
172 MB in 3.01 seconds = 57.05 MB/sec is ok.Setting multcount to 16
would increase 10 %,or less.

---

### Post by LingaringBell on 2009-08-11
I copied a 7.8 GB file, it copied at about 30.3 MB/sec.  I tried to type this post while it was copying and it took forever, the screen would freeze for a moment or the firefox window would turn gray (I think that means it is processing?).  It just doesn't seem normal to me at all.

---

### Post by alecz20 on 2011-03-20
> **LingaringBell said:**
> I copied a 7.8 GB file, it copied at about 30.3 MB/sec.  I tried to type this post while it was copying and it took forever, the screen would freeze for a moment or the firefox window would turn gray (I think that means it is processing?).  It just doesn't seem normal to me at all.

I have the exact same behavior.

It only occurs If I am copying internally (within the same computer), regardless if from to same drive or different drives.

However, if I copy to a computer on the network (at about 15MB/s) there are no system slowdowns.

I noticed in system monitor that there is a lot of CPU IO wait.

---

