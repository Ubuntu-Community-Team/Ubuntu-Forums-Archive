---
title: "USB External Hard Drives: Pros vs. Cons?"
date: 2010-10-31
forum: Hardware
---

### Post by mr_luksom on 2010-10-31
I'm scoping out a mythTV setup with ubuntu, and I have been looking at storage.

I wanted to RAID together a few medium sized drives (500GB - 1TB), and I'm trying to figure out what to buy.

When I go to price drives, USB external drives seem to be cheaper per GB than internal drives (at least where I am looking) - I don't really understand this (as there should be an internal drive inside the enclosure right?).

So other than the obvious problems with usb external drives (damage during transit, cooling - which will not apply to a static myth setup), what are the pros and cons of usb drives?

---

### Post by efflandt on 2010-10-31
Drives in an external USB enclosure do not have to be that fast, because speed is limited by USB 2.0 (unless you get eSATA, or your computer and drive have USB 3.0).

Not sure of maximum speed for USB 2.0, but for WD Passport hdparm -t typically shows ~32 MB/sec.  So USB does not have to use the newest hottest drives.  That is about 1/4th the speed of a typical desktop 7200 RPM SATA II drive (hdparm -t for my desktop is ~117 MB/sec).

I was quite surprised that hdparm -t for my 4 year old laptop with SATA I was only USB speed (~31 MB/sec).  That 160 GB drive only runs 4200 RPM.  When I tried SSD in my laptop it was 120 MB/sec.  When I put that Intel SSD in my desktop with SATA, II its read speed was 250 MB/sec.

Anyway the speed limit of USB 2.0 probably explains why you can buy a USB hard drive for less than a new drive and USB enclosure (because it does not need to be any faster than USB).  Although, with eSATA you can get up to SATA II speeds from external drives.

---

### Post by mr_luksom on 2010-11-01
I think the transfer speed has scars me off using USB devices for this. I tested the USB hard drive I already have with hdparm -t and it only got to 11MB/s!

That is probably more than enough for what I want to do, but it's not  exactly futureproofed.

Thanks heaps.

---

