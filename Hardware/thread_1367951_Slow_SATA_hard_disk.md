---
title: "Slow SATA hard disk"
date: 2009-12-30
forum: Hardware
---

### Post by mattjubb on 2009-12-30
Hi Guys,

Sorry for my first post being a plea for help but Ive been using ubuntu with no problems for years but this one has me completely stumped. Id really appreciate any help/advice you can give.

I have two SATA hard disks:
/dev/sda - Samsung spinpoint 1TB
/dev/sdb - Hitatchi deskstar 2TB

sda is the boot disk with my /home etc, sdb has loads of data. 

My problem is that the speed for any kind of file transfer that involves sda is like 5MB/s but when its with sdb then i get 50-60MB/s. I know the drive is capable of so much more because of the results I get from hdparm

/dev/sda:
 Timing cached reads:   2224 MB in  2.00 seconds = 1112.88 MB/sec
 Timing buffered disk reads:  292 MB in  3.00 seconds =  97.25 MB/sec

hdparm -i gives

/dev/sda:

 Model=SAMSUNG, FwRev=1AG01118, SerialNo=S1VSJ9BS5*****
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=32767kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

For reference sdb's details are:
 Timing cached reads:   2136 MB in  2.00 seconds = 1068.66 MB/sec
 Timing buffered disk reads:  388 MB in  3.01 seconds = 128.75 MB/sec

 Model=Hitachi, FwRev=JKAOA10D, SerialNo=JK1121YA*****
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=56
 BuffType=DualPortCache, BuffSize=30011kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=3907029168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

Ive tried everything - changing filesystem ext3 -> ext4, switching sata cable, switching sata connector. Nothing seems to have any effect and im always moving files at 5MB/s

Thanks
Matt

---

### Post by TheGoshem on 2009-12-30
I get similar results...
Just transfered a 6GB file from one drive to another and it went at about 6MB/s

```
greg:~$ sudo hdparm -Tt /dev/sda1
[sudo] password for greg: 

/dev/sda1:
 Timing cached reads:   5804 MB in  2.00 seconds = 2904.73 MB/sec
 Timing buffered disk reads:  216 MB in  3.01 seconds =  71.71 MB/sec
greg@Gnobes-Desktop-P5N32:~$ sudo hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:   7914 MB in  2.00 seconds = 3963.13 MB/sec
 Timing buffered disk reads:  100 MB in  1.60 seconds =  62.56 MB/sec
```

Also, i have a gentoo samba share on my network (gigabit) and i can only transfer at 5-6MB/s to my samba share, but under Windows 7 (64bit) im hitting close to 40MB/s...

Using onboard nic: Asus P5N32-E SLI


Any ideas?!

---

### Post by ze_otter on 2010-01-18
Slow SATA transfer speeds seem to be a recurring problem, but no one seems to know anything helpful about it. I just built a new dual core 64-bit system and installed 9.10 on it, but the extremely slow SATA speed is starting to get to me. For me, it often starts nicely enough, but then it keeps stalling continuously so that the average speed is nothing worth mentioning. It also tends to make the entire system unresponsive whenever it stalls, so it's getting more than a bit annoying...

---

### Post by welchy on 2010-03-04
Agree its a recurring problem.

See this thread for some details : [http://ubuntuforums.org/showthread.php?t=1150108](http://ubuntuforums.org/showthread.php?t=1150108)

Using HDPARM to test harddisk speed is not very useful though.

The best thing to do is to bring up a command shell and time a copy of a large file

EG : time cp <largeFile> <dest> 

Where the file is large (around a gig is good) and the source and dest drives are physically different.

On the same machine, I get 60-70mb per second with Debian, 60-70mb per second with Mint 8.0 and I used to get 5-10mb per second with Ubuntu 9.4

Never tried 9.10, but mint 8 is essentially 9.10 and it seems to be fine so far (just installed this morning)

For reference mine looks like this :

# ls -ltrh bigfile.avi 
-rw-r--r-- 1 user user 1.4G 2009-11-29 00:06 bigfile.avi
# time cp bigfile.avi /home/filecopytest/

real	0m23.790s
user	0m0.030s
sys	0m3.820s

# time sync

real	0m0.197s
user	0m0.000s
sys	0m0.000s


So 1400mb in 23 seconds, roughly 60mb per second. Around what I would expect for a normally working (but not tuned) system.

What results do you get in a similar test ?

---

