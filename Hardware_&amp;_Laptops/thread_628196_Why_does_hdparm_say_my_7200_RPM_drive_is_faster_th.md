---
title: "Why does hdparm say my 7200 RPM drive is faster than my 5400 RPM drive?"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by Levander on 2007-12-01
I've got an old dual PIII 550 machine that I've just put Mythbuntu on.  Everything is running fine except for when I use the Picture in Picutre feature.  It's like the video is skipping, and mythfrontend.log says I'm getting "prebuffering pauses".  Asking in #mythtv-users on freenode, they've suggested the problem might be my hard disks....

I've got a Maxtor Fireball 3 model #2F040L0 hooked up as my primary master, and a Seage Barracuda IV model #ST380021A hooked up as a secondary master.  The specs o the two drives are pretty much identical, except the Fireball has is supposed to be 5400 RPM and the Barracuda is supposed to be 7200 RPM.

Specs for the Fireball: [http://computers.pricegrabber.com/hard-drives/m/615456/details/](http://computers.pricegrabber.com/hard-drives/m/615456/details/)
Specs for the Barracude: [http://computers.pricegrabber.com/hard-drives/m/462162/details/](http://computers.pricegrabber.com/hard-drives/m/462162/details/)

I'm putting them on different IDE ribbons (note the primary and secondary designations above) to try to get faster performance out of my disks, so maybe MythTV will work better.

But, according to the very simplistic benchmark 'hdparm -tT', the Fireball is performing much better.

IIRC, the performance numbers were very similar when the Barracuda was the primary slave also.

Here are the numbers:

```

levander@bread:~$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   256 MB in  2.00 seconds = 127.86 MB/sec
 Timing buffered disk reads:   86 MB in  3.04 seconds =  28.31 MB/sec

levander@bread:~$ sudo hdparm -tT /dev/sdb
/dev/sdb:
 Timing cached reads:   264 MB in  2.01 seconds = 131.40 MB/sec
 Timing buffered disk reads:   54 MB in  3.04 seconds =  17.77 MB/sec

levander@bread:~$ sudo hdparm -i /dev/sda
/dev/sda:

 Model=Maxtor 2F040L0                          , FwRev=VAM51JJ0, SerialNo=F173XK6E            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=80293248
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


levander@bread:~$ sudo hdparm -i /dev/sdb
/dev/sdb:

 Model=ST380021A                               , FwRev=3.05    , SerialNo=3HV08AB5            
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5

 * signifies the current active mode

levander@bread:~$ 

```

---

### Post by tgalati4 on 2007-12-01
Both drives have a 2 MB cache.  The 7200 RPM drive is 80 GB and the 5400 RPM drive is 40 GB.  Perhaps the layout of the platter and heads in the Fireball allow for greater performance.

Only one drives specifies the seek time of 9.5 ms, so it's a guess as to what is causing the real difference.

Do you have an 80-pin cable to connect the drives?  You should be able to push mode udma5 to get more drive performance.  

I would think that the graphics card is causing the skipping.  If you have on-board Intel graphics, then they basically suck.  You need a real graphics card to drive PIP.  Anything else is painful.

---

### Post by Levander on 2007-12-01
Guess I should mention that even though they are both ATA133 drives, they are connected to a motherboard based on the Intel 440BX chipset.  So, the motherboard's IDE controller only supports up to ATA33.

---

### Post by Levander on 2007-12-01
> **tgalati4 said:**
> Perhaps the layout of the platter and heads in the Fireball allow for greater performance.
Yeah, I guess I'm looking at the specs pretty simplisticly.  The Barracuda I got does have two platters.  From [http://www.storagereview.com/articles/200109/20010918ST380021A_1.html](http://www.storagereview.com/articles/200109/20010918ST380021A_1.html)

> **StorageReview]In the tradition of the Barracuda name, Seagate's latest, of course, features a 7200 RPM spindle speed. The drive is available in one- and two-platter configurations, yielding a flagship capacity of 80 GB. Interestingly, the two-platter models are spec'ed with a 9.5 millisecond access time while the one-platter units are marked at 8.9 ms. A 2-megabyte buffer rounds out the package. [/QUOTE]

If you look at that page, 80 GB was the largest Barracuda IV Seagate offered at the time, so you figure that the 80 GB has two platters.

[QUOTE=tgalati4 said:**
> Only one drives specifies the seek time of 9.5 ms, so it's a guess as to what is causing the real difference.  I don't see where that 'hdparm -i' output specifies 9.5 ms seek time on either drive.  I rarely use hdparm, so I probably just can't find it in the output.  Note that that quote from Storage Review above says the Barracuda has a 9.5 ms access time, if that's interesting.

> **tgalati4 said:**
> Do you have an 80-pin cable to connect the drives?  You should be able to push mode udma5 to get more drive performance.  
I'm about to try udma5...  Not sure exactly what it does, but I'll try figuring out hdparm enough to set it.  And yeah, there's an 80 pin cable now.  When I moved the Barracuda IV to be the secondary master, I just used the ribbon that was plugged into my DVD drive, it was a 40 pin.  Tinkering around with it now, I've replaced that ribbon with an 80 pin.  'hdparm -tT' reported similar numbers with both the 40 pin and 80 pin cable.  Probably because even though the drives are ATA/133, the mother board only support ATA/33.

> **tgalati4 said:**
> I would think that the graphics card is causing the skipping.  If you have on-board Intel graphics, then they basically suck.  You need a real graphics card to drive PIP.  Anything else is painful.
It's an nVidia 6200 video card.  No one mentioned that as maybe being the problem.  And, I think I've talked to others who are using the same video card for PiP (picture in picture).  Next time I'm in the freenode channel though, I'll ask.

---

### Post by Levander on 2007-12-01
I figured out where you got the 9.5 ms access time from, it was from the specs I posted a link to on pricegrabber.

I found better specs for the Fireball 3, from CNET:

[http://reviews.cnet.com/hard-drives/maxtor-fireball-3-hard/4507-3186_7-20438125.html?tag=sub](http://reviews.cnet.com/hard-drives/maxtor-fireball-3-hard/4507-3186_7-20438125.html?tag=sub)

And, from CNET for the Barracuda IV:

[http://reviews.cnet.com/hard-drives/maxtor-fireball-3-hard/4507-3186_7-20438125.html?tag=sub](http://reviews.cnet.com/hard-drives/maxtor-fireball-3-hard/4507-3186_7-20438125.html?tag=sub)

Note that CNET's listed specs are that the Barracuda IV has a 9.5 ms seek time, and the Fireball 3 has a 12 ms seek time.

I'm guessing seek and access are synonyms in this context?

No word on how many platters the Fireball 3 has.

---

### Post by popch on 2007-12-02
'RPM' stands for rounds per minute. One platter turns at 5400 RPM, the other at 7200 RPM. Both store data at the same angular distance (or resolution, if you will). The one which turns faster transfers more data within the same time as the other one. It is, in fact, faster. Much as your bicycle runs faster if the wheels turn faster.

---

### Post by tgalati4 on 2007-12-02
The Intel 440BX chipset is slow by today's standards.  And you are correct, you are limited to 33 MHz (udma2) transfer speed (vs ATA133 udma5 or udma6).  Perhaps the nVidia card is limited by the data bus as well.  This would cause flickering.  Try xbench and run your card through some testing and you will see the bottlenecks.

An 80-pin cable will get you 66 to 133 MHz speeds, but only if your motherboard supports it.  Otherwise you are stuck with 33 MHz or roughly 33 megabytes/sec data transfer.  High quality video needs more than that, check the gamer forums.  So I would say your aging motherboard  is the bottleneck.

Linux chooses the highest performance available for each drive.  Messing with hdparm only tends to degrade performance in my opinion.  I've never been able to get more performance out of a drive with an hdparm switch.  I've tested several drives, so this convinces me that the current hardware detection does a decent job in optimizing drives.

Your performance is-what-it-is.  I have an old Dell with an Intel 440BX chipset and my video flickers as well.  With a PIII/500 MHz and on-board S3 video--DVD playback is marginal with 100% CPU load.

---

### Post by Levander on 2007-12-02
> **tgalati4 said:**
> The Intel 440BX chipset is slow by today's standards.  And you are correct, you are limited to 33 MHz (udma2) transfer speed (vs ATA133 udma5 or udma6).  Perhaps the nVidia card is limited by the data bus as well.  This would cause flickering.  Try xbench and run your card through some testing and you will see the bottlenecks.

I snipped the rest of that reply...

Wow, with these last two posts, this thread is really getting off of what I was asking about.

---

### Post by Whiffle on 2007-12-02
You might try some hdparm tuning:

[http://www.usalug.org/phpBB2/viewtopic.php?p=33142](http://www.usalug.org/phpBB2/viewtopic.php?p=33142)


Looks like udma2 is the best that chipset can do, that may be part of your problem.  However I would still think the 7200 rpm drive would be at least equal to the 5400 rpm.

Could you post the output of hdparm -I for both drives?

---

### Post by Levander on 2007-12-04
Thanks Whiffle.  I had been looking for a good hdparm tutorial.  That looks like exactly what I need.

---

### Post by Yellow Pasque on 2007-12-04
> **Levander said:**
> I snipped the rest of that reply...

Wow, with these last two posts, this thread is really getting off of what I was asking about.
Didn't you ask why the 5400RPM Fireball was performing better than the 7200RPM Cuda? The posts above are telling you why; the mobo's IDE bus is too slow. If it's saturated with data, it makes sense to me that the primary IDE device would get priority.

Personally, I think you're spinning your wheels trying to tune with hdparm, but I wish you luck nonetheless.

---

