---
title: "IBM600X - CD Access Locks-up system"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by dnsauve on 2005-09-12
I installed Ubuntu 5.04 this weekend onto an older IBM 600X laptop.  I must say, I was impressed.  The install went fairly smooth (apart from having to add irqpoll to my boot paramaters or be stuck looking at a black screen with a cursor) and I was up and running in no time.

I used the laptop all weekend for work and find I've been just as productive, if not more, then when I was using Windows XP.

At least until I decided to listen to an audio CD.  About 10 seconds into the first track, the computer locks up.  Completely, and irrevocably.  CTR+ALT+BKSP does nothing, reset does nothing.  The only way to get control back is to hold the power button down to force a shutdown.

The same thing happens when I try to transfer files from a CD-ROM.  The time it takes to lockup varies, but it's usually about 10 seconds.  This is doubly strange, because I installed the system from CD-ROM without any issue.

I've verified that DMA is off, but I'm not sure what else to look at.  It's been about 9 years since my last serious Linux experience.

Any help would be appreciated.

Thanks,
David

---

### Post by dnsauve on 2005-09-13
I've experimented a bit with hdparm, changing the DMA modes of the drive, but this seems to only make minor differences in the time it takes to lockup after.

I tried *hdparm -X sdma0 /dev/cdrom*, this seemed to help.  The audio CD I tested played fine for over 30 seconds before locking up the whole system when I hit the "fast-forward" button.

---

### Post by dnsauve on 2005-09-14
Okay.  I've now upgraded the BIOS to the latest version from IBM.  I've also upgraded the CDROM firmware to the latest version as well.

I've even tried swapping the drive with another one.

Still the same lockup after 10-30 seconds.

---

### Post by dnsauve on 2005-09-14
Gave up and re-installed Ubuntu.  Same thing.  I'm out of ideas here and it doesn't look like anybody is even reading these posts...

---

### Post by dnsauve on 2005-09-15
Would it help if I posted the results of dmesg, hdparm, or some other utility?

---

### Post by dnsauve on 2005-10-06
In case anyone is interested, the solution is to enable dma on the cd-rom.

It works perfectly now.

---

