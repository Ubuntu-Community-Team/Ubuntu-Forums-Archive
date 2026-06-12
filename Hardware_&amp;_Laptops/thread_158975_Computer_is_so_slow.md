---
title: "Computer is so slow"
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by zugvogel on 2006-04-12
Hello. I've had this problem for a long time but it's really beginning to annoy me now. Basically, Ubuntu runs very slowly. Problems Include:

- A good 10-second delay when opening the gnome menu for the first time
- Evolution taking a minute to start
- OpenOffice taking at least one minute to start
- Black lines every time I minimise and maximise a window
- Terminal taking at least 5 seconds to start

My computer specs are:

- Acer laptop
- 256MB RAM
- Mobile Intel Celeron 2.0GHz

uname -a gives:
Linux degen 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux

I had the 686 kernal before but this made no obvious difference. It's just 386 now because I re-installed Ubuntu recently.

Free gives:
             total       used       free     shared    buffers     cached
Mem:        248292     242164       6128          0       9740      46840
-/+ buffers/cache:     185584      62708
Swap:       730948      79492     651456

more /proc/meminfo gives
MemTotal:       248292 kB
MemFree:          7280 kB
Buffers:          9600 kB
Cached:          53476 kB
SwapCached:      14464 kB
Active:         135340 kB
Inactive:        16552 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       248292 kB
LowFree:          7280 kB
SwapTotal:      730948 kB
SwapFree:       651756 kB
Dirty:              12 kB
Writeback:           0 kB
Mapped:         122428 kB
Slab:            23652 kB
CommitLimit:    855092 kB
Committed_AS:   369396 kB
PageTables:       1604 kB
VmallocTotal:   778232 kB
VmallocUsed:      6216 kB
VmallocChunk:   771700 kB

Although they suggest that I have used all the RAM, I've heard that linux does that anyway so I'm not sure how reliable that is. Could it be a case that I need more RAM?

Basically, my question is: What do I need to do to get the menu to open instantly, the black lines to stop showing, oowriter to open within 15 seconds or so (at work it opens within 4 seconds...)

Any advice would be appreciated. Thank you!

---

### Post by Sef on 2006-04-12
I would either get more ram or install xubuntu.

Install Xubuntu:

sudo apt-get update

sudo apt-get install xubuntu-desktop

Xunbuntu is a lightweight desktop, so it would be faster on your computer than gnome is.

You could run both Gnome (or KDE) and Xubuntu.  You simply choose the one you want at login. (under sessions.)

---

### Post by Syman on 2006-04-12
I've heard about some programs which can make your PC work faster.
But I've never tried them.

---

### Post by sublime on 2006-04-12
your problem is the ram.  256mb isnt really enough to run most modern programs ata sufficent speed.  i would go at least 512 or 768 wit 1gb being prefered

---

### Post by sublime on 2006-04-12
hte problem is your ram or lack thereof.  256 isnt really enough to run most modern programs at a decent speed.  i would go with 512 or 768 at the least wth 1gb being the prefered amount

---

### Post by xXx 0wn3d xXx on 2006-04-12
Try these:
1. Prelink
2. InitNG (Search the Ubuntu Wiki)
3. Disable unneeded services from starting
4. A lighter DE
5. Tweak your ext3 filesystem for a performance boost.

Search for all of that and you will improve your computers speed by alot. :)

256 mb of ram is enough to run Gnome. It may also be a video/hardware problem. I was running Gnome on a 400mhz, 8 mb video card, and 128 of ram and Gnome ran fairly well.

---

### Post by zugvogel on 2006-04-14
Many thanks to all of you for your comments. I'm loath to buy more RAM since my laptop is slowly dying (did I mention?: Never buy acer (they're cheap, but their repair centre is completely incompetent, at least in the uk...)). I'd never heard of this pre-linking but that sounds like just what I'm looking for. If that doesn't do the trick then I'll look further such as the ext3 adjustments or finally Xubuntu (although I like gnome a lot).

Thanks!

---

### Post by coolclassic on 2006-04-14
Another suggestion is check your hdparm you may not have dma active which will slow down hd accessing.

Do the following to see if dma is active:

sudo hdparm /dev/hda (your drive)

If its not then

sudo hdparm -d1 /dev/hda   (to set dma)

To check speed improvements you can do the following before and after:

sudo hdparm -tT /dev/hda

---

