---
title: "Slow hard drives"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by super.rad on 2007-10-30
I've had this problem since edgy, the whole system seems to be really slow and i think it's the hard drives causing it, everything slows down even more when doing certain tasks (such as checking a torrent file or amarok updating my music collection).
In system log whenever i boot up i get the following messages in "kern.log" "messages" and "syslog"
> Oct 30 20:45:26 jimin-desktop kernel: [   55.312000] hda: dma_intr: bad DMA status (dma_stat=76)
> Oct 30 20:45:26 jimin-desktop kernel: [   55.312000] hda: dma_intr: status=0x50 { DriveReady SeekComplete }
> Oct 30 20:45:26 jimin-desktop kernel: [   55.312000] ide: failed opcode was: unknown
The same comes up for hdb (i have two hard drives installed) and those 3 messages repeat for a while and then this comes up
> Oct 30 20:45:41 jimin-desktop kernel: [   69.256000] hda: DMA disabled
> Oct 30 20:45:41 jimin-desktop kernel: [   69.592000] ide0: reset: success

Here is some information about my hard drives:
```
jimin@jimin-desktop:~$ hdparm -i /dev/hda
/dev/hda:

 Model=ST3160021A, FwRev=8.01, SerialNo=5MT25XGH
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

jimin@jimin-desktop:~$ sudo hdparm -Tt /dev/hda

/dev/hda:
 Timing cached reads:   1622 MB in  2.00 seconds = 811.74 MB/sec
 Timing buffered disk reads:    4 MB in  3.82 seconds =   1.05 MB/sec
```

```
jimin@jimin-desktop:~$ sudo hdparm -i /dev/hdb

/dev/hdb:

 Model=Maxtor 4D080H4, FwRev=DAH017K0, SerialNo=D41VKJ3E
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160086528
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 0:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

jimin@jimin-desktop:~$ sudo hdparm -Tt /dev/hdb

/dev/hdb:
 Timing cached reads:   1592 MB in  2.00 seconds = 795.73 MB/sec
 Timing buffered disk reads:    4 MB in  3.76 seconds =   1.06 MB/sec
```

Can anyone see anything wrong there which would explain why my computer seems to be running slow, if you need any more information just ask. Thanks

---

### Post by Linicks on 2007-10-30
The first area to look at this is renew the IDE cables (80-wire) - or at least unplug and  re-seat them all .  Also check that they are not wrapped/about power cables.

Nick

---

### Post by super.rad on 2007-10-30
Already tried new IDE cables, unplugged and re-seated them. They aren't wrapped around anyother cables either.

---

### Post by Linicks on 2007-10-30
Very strange.  Are they master/slave or cable select?

Also doing the bug report is well worth a post to the linux-ide mailing list in issues like this.


Nick

---

### Post by super.rad on 2007-10-30
They are master/slave.

Never filled in a bug report before but i shall have a look and try to work out how to do it.

---

### Post by Linicks on 2007-10-30
Just send a mail to:

[email]linux-ide@vger.kernel.org[/email]

with a suitable subject.

Ask to be CC'ed as you are not on the mailing list (so you get replies) - if you subscribe, you will get 100's of mails a day.

Then do similar debug logs and descriptions into the mail like you did here.

Somebody (hopefully) will pick it up and help you to debug.

e.g.  Over the years I have posted to LKML a lot - 90% of the time you get somebody to help if you should there be an 'issue' and not a newbie problem.

My most recent was a new DVD drive... it turns out the firmware in this drive reports wrongly - I got a result and thus a patch got put into the kernel!

Read from bottom up:

[http://marc.info/?t=119272906500002&r=1&w=2](http://marc.info/?t=119272906500002&r=1&w=2)

Nick

---

### Post by super.rad on 2007-10-30
I've sent an email so wait to hear back now. Thanks

---

### Post by Linicks on 2007-10-30
You should have also said you changed cables, /master/slave, etc. but they will worm that out of you anyway...

Nick

---

### Post by dabl on 2007-10-30
In BIOS, sometimes there are multiple "mode" choices for your IDE drives.  Do you have that?  What mode are they set to?

---

### Post by Linicks on 2007-11-01
Super.rad - I see somebody (Alan Cox, no less)  has replied to your kernel post asking for more in formation.

[http://marc.info/?t=119378444800003&r=1&w=2](http://marc.info/?t=119378444800003&r=1&w=2)

Nick

---

### Post by super.rad on 2007-11-05
No the BIOS on my motherboard doesn't have many options. I've tried looking for an updated BIOS but can't find any.

---

### Post by super.rad on 2007-11-15
OK so apparently the problem is the kernel is switching from DMA to PIO
and i have an ATIIXP controller (built into the chipset)
Does anyone have any solutions to how i can get DMA working? Thanks

---

