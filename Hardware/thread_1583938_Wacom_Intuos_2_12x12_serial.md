---
title: "Wacom Intuos 2 12x12 serial"
date: 2010-09-28
forum: Hardware
---

### Post by Markopotamus on 2010-09-28
I'm running 10.04 on a PC, and am attempting to use my graphics tablet. It's a Wacom Intuos 2 12x12 serial tablet, connected via a serial PCI expansion card; but no joy. The tablet is on and the light on the tablet responds when the pen makes contact, but no response on-screen. 

**xsetwacom list** outputs nothing at all. 

I was wondering if there's any way, by hook or by crook, It could be coaxed into action? Then, if I could get my Canoscan 700F scanner working, I'd be absolutely sorted with Ubuntu!

---

### Post by Favux on 2010-09-28
Hi Markopotamus,

Welcome to Ubuntu forums!

There may be a chance of getting your serial Wacom tablet working.  Serial support was dropped in Lucid's xf86-input-wacom.  But that was due to lack of developer time, not policy.  A couple of patch sets were submitted to restore serial tablets to xf86-input-wacom and a few folks have got their tablets working with both patch sets.  See the paragraph starting with the red line near the top of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Unfortunately nothing's happened on that front in a while.

Hope this helps.

Good luck!

---

