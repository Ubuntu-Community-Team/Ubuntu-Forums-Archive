---
title: "[SOLVED] Card Reader Extremely Slow"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Sutur on 2007-10-31
Hello,

I have a generic brand card reader. Linux detects the reader and all card plugged in. It can recognise, mount, read & write to any card inserted. The only problem is that it's very, very slow.

A 4MB file may take up to a minute and a half (roughly).

I have checked the BIOS, and USB 2.0 is enabled - all other USB ports are fine and very quick to read/write.

The reader sits in a 3.5" floppy bay and connects to my board through on-board USB (normally used for front panel case USB ports). I've tried a different on-board plug, but it didn't help.

It used to be fine but I noticed that it isn't working properly in Windows either. I suspect it's very likely something to do with setting on my **motherboard's BIOS**,

But I don't understand how the unit works exactly so I am unable to locate any clues as to how I can fix it.

Any help would be much appreciated.

**OS**: Ubuntu 7.10
**Board**: ASUS A8N-SLI Premium
**CPU**: AMD Dual Core 3800+
Latest BIOS installed from ASUS.

---

### Post by Sutur on 2007-11-01
Bump for help.

---

### Post by Sutur on 2007-11-01
Another bump.

---

### Post by Sutur on 2007-12-06
Miraculously solved after having a different problem where pcmanfm was somehow unable to mount/unmount drives/media.

I installed **pmount**, which simultaneously fixed both problems. Read/write speeds are roughly 20 times faster, and I am able to use pcmanfm properly too.

I hope this helps someone in future because it was a pain in the *** for me.

I'm marking this thread solved now.

---

