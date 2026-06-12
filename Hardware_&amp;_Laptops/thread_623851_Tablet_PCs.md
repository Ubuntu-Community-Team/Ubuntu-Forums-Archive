---
title: "Tablet PCs?"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by Tylerofl on 2007-11-26
I was looking at getting one of those HP TX1000Z tablet PCs. I'm sure Ubuntu will work on it like any other laptop, I'm just wondering if it will be able to make use of its media card readers, fingerprint capture, and most importantly, stylus/touch screen. Does anyone else have Ubuntu on a laptop like this?

---

### Post by MadMax08 on 2007-11-26
i have 7.10 64-bit running on my tx1110. you need a few boot parameters to have it boot correctly, wireless worked out of box, sound worked with some tweaks, webcam works out of box, card reader works out of box.

i used this thread a lot for fixes:

[http://ubuntuforums.org/showthread.php?t=442483](http://ubuntuforums.org/showthread.php?t=442483)

i have yet to get my headphone jack, fingerprint reader, and webcam microphone working, but i dont need them that bad.

good luck!

---

### Post by Tylerofl on 2007-11-27
Does the stylus work?

---

### Post by Griff on 2007-11-28
I was looking at the HP TX1205US.  I'd be interested in what works here.  I was seriously considering getting it until i realized it was a tablet.  I thought that might cause more problems than it'd be worth.  Windows is not an option for me.

---

### Post by Griff on 2007-12-02
Well, I got the model without the touchscreen.  I figured it'd just cause problems and it was something I was never really interested in.  I just liked the size and other features.  Windows performs like crap on it.  There's a lag for everything I do.  Also (prepare youself this is pretty funny), when I plugged in my usb mouse it broke the drivers for the touchpad and I had to reinstall them.  The live cd works for me when I added 'noapic vga=0x317' to the boot line.  It's installing right now, I report back what has worked out of the box for me (hp pavilion tx1000 line, more specifically hp tx1205us).  Though I can't say anything about the touchscreen the rest of the hardware should be the same or similar.

---

### Post by baxterdog on 2007-12-02
My experience with all things HP has been touchy. They don't respond favorably to settings changes. As in changing the IP doesn't stick through reboots and the drivers are quarky. (is that a word?)

---

### Post by olejorgen on 2007-12-02
If the stylus is a wacom-type, you can be pretty sure it'll work.

---

### Post by Griff on 2007-12-04
On my hptx1205us I have had no issues thus far with 64 bit gutsy (although there have been warnings about using gutsy with hp laptops).

The install cd will run with 'noapic vga=0x317' appended to the boot line (note this needs to be made permanent after installation)
The nvidia proprietary driver gutsy installed for use with compiz-fusion runs with no issues.
Compiz-fusion runs flawlessly with no slowdown.
Wireless was a piece of cake (no, really, it was).  I downloaded the 32 bit drivers from hp's website then used this method (scroll down to Broadcom BCN4311): [http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A](http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A)

I absolutely love this laptop.

---

### Post by borahshadow on 2008-02-02
> On my hptx1205us I have had no issues thus far with 64 bit gutsy (although there have been warnings about using gutsy with hp laptops).

The install cd will run with 'noapic vga=0x317' appended to the boot line (note this needs to be made permanent after installation)
The nvidia proprietary driver gutsy installed for use with compiz-fusion runs with no issues.
Compiz-fusion runs flawlessly with no slowdown.
Wireless was a piece of cake (no, really, it was). I downloaded the 32 bit drivers from hp's website then used this method (scroll down to Broadcom BCN4311): [http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A](http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A)

I absolutely love this laptop.

How well do things like suspend to RAM work and things like the card reader, fingerprint scanner, and webcam work?
And other than the things you mentioned everything worked out of the box? are there any downsided to the noapic boot parameter like does it not scale the cpu or anything? I've heard that this laptop gets hot is that true?

---

