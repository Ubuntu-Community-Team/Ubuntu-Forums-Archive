---
title: "TV Out with Ati IGP 320M"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by celloandy on 2005-07-08
I recently bought a cheap laptop with an Ati IGP 320m (aka Mobility U1) integrated graphics card, and have been trying to get tv out working with it.  After tinkering with the atitvout tool for a while, I've gotten it working (sort of).  As long as I'm working with a plain text console or something that outputs to VESA (including X with the VESA driver), I can get atitvout to recognize that my TV is attached, and let me switch to TV mode (X with the radeon driver doesn't work, but that's okay with me).  My problem is that the colors aren't right.  At first, I thought the output was black and white or grayscale, as the results from "ls" weren't colored on my TV, but some bright colors do appear colored on the screen, but they're just really dull-looking.  Bright red (#FF0000) appears brownish, bright blue is a dark navy color, etc.  I'm really frustrated, and was wondering if anyone knew how to tweak the colors output by VESA so that they look semi-normal on the TV.

Andrew

(Oh, and other potentially relevant info: I'm not using the ATI proprietary drivers because they don't support this chipset.  Also, my computer's TV out is S-Video, but my TV only has composite, so I'm using an S-Video to Composite converter, but I used this same converter with another computer with an nVidia card, and it worked fine, so I don't think the converter is causing the problem.)

---

### Post by celloandy on 2005-07-09
Guess nobody knows about this here, huh?  Maybe I'll try the Gentoo forums...

Andrew

---

### Post by www.rzr.online.fr on 2008-04-05
> **celloandy said:**
> Guess nobody knows about this here, huh?  Maybe I'll try the Gentoo forums...

Andrew

It used to work on debian, see :

[http://rzr.online.fr/q/vbe](http://rzr.online.fr/q/vbe)

---

