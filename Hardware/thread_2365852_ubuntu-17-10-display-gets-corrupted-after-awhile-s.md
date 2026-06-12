---
title: "ubuntu-17-10-display-gets-corrupted-after-awhile-sometimes"
date: 2017-07-11
forum: Hardware
---

### Post by batgirl2 on 2017-07-11
My Panasonic Toughbook (32-bit) running 17.10 (I use Xorg as Wayland  has problems with cursor being weird and unusable) will boot up fine and  most of the time all is fine (and awesome!)... BUT, about every third  time or so it will boot up, you'll be browsing or looking at files in  nautilus, or sometimes just doing nothing, and the screen will turn into  this kaleidescope of colors, go blank for a couple of seconds, the back  to the horizontal kaleidescope lines of color, go blank, lines of  color, etc. Nothing except hitting the power button and rebooting gets  it back to normal. 

  
Only started this about a couple of weeks after upgrade to 17.10. Did  my video card suddenly decide to begin flaking out coincidentally after  the upgrade, or did one of the updates in the past week or so mess up  the video driver or something? I did check to see if display (settings,  devices, color) was calibrated (used D65).

---

### Post by efflandt on 2017-07-11
You cannot use pcmcia-cs anyway with current kernels, [http://pcmcia-cs.sourceforge.net/](http://pcmcia-cs.sourceforge.net/) says **The Linux pcmcia-cs package is officially deprecated.  It can only be used with 2.4 and older kernels.** You might see if you can find anything helpful in the HOWTO [http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO.html](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO.html)

You might already have pcmciautils, or at least my 16.10 does by default (I did not add it). It is my understanding that pcmcia support has been built into kernel since 2.6 kernel which is why this shows 2.6:```
~$ dpkg-query -l pcmcia* | grep ii
ii  pcmciautils    018-8        amd64        PCMCIA utilities for Linux 2.6

~$ apropos pcmcia
lspcmcia (8)         - display extended PCMCIA debugging information
pccardctl (8)        - PCMCIA card control utility
```

---

### Post by pdc on 2017-07-11
is this your camera? [http://uk.pcmag.com/consumer-electronics-reviews-ratings/69489/gallery/7-funky-digital-cameras-from-the-90s?p=3](http://uk.pcmag.com/consumer-electronics-reviews-ratings/69489/gallery/7-funky-digital-cameras-from-the-90s?p=3) it has done very well

---

### Post by kurt18947 on 2017-07-12
A very long shot probably but have you looked at the "40 in 1" type card readers? I've only heard of pcmcia slots in laptops of a certain vintage i.e. pre-pc card machines but not on other peripherals.

Edit: a few minutes on Ebay shows PCMCIA to USB card readers.  You'd need to be careful to get the reader you need, not the later generation card reader. Here might be a candidate:

[http://www.ebay.com/itm/PCMCIA-Flash-Disk-card-Reader-ATA-Memory-Card-To-USB-2-0-Adapter-converter-/191114594282](http://www.ebay.com/itm/PCMCIA-Flash-Disk-card-Reader-ATA-Memory-Card-To-USB-2-0-Adapter-converter-/191114594282)

Expensive little bugger though. I dislike posting Ebay URLs because they're transient but  perhaps this will give you a place to start.

---

### Post by kurt18947 on 2017-07-13
I haven't messed with anything PCMCIA in years so I have no recent experience with it. If they weren't so bloomin' expensive, I'd still be tempted by the PCMCIA -> USB route, I haven't had USB issues (except with a MATE distro when MATE was new) in a long time. As long as you can get the pics off I guess that's what matters.

---

### Post by kurt18947 on 2017-07-15
5 1/4" floppy drive? That **is** hardcore:KS.

---

