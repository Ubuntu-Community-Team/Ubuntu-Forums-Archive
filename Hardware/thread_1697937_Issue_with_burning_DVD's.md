---
title: "Issue with burning DVD's"
date: 2011-03-01
forum: Hardware
---

### Post by Mystro256 on 2011-03-01
I'm not sure what the issue is but as long as I have had my current desktop, I have been unable to burn DVD's. I replaced my old dvd burner (PATA) with a SATA one but doesn't seem to make a difference. CD's burn quite well, besides the fact it tells me to manually eject it at the end, which I don't mind.

I make this desktop myself, out of an ASUS board and a Intel Duo I bought from a computer shop new. The current burner is a super writemaster. This desktop has only had Linux on it, originally Debian but I moved to Ubuntu when 9.04 came out. I tried brasero, gnomebaker and another I can't remember the name, not k3b. The problem is consistent over Debian/Ubuntu and both burners, so I would guess it's a Linux issue with my board. That or perhaps a bios/cmos setting?

My biggest problem is that I don't know exactly what the issue is; the error given is vague, such as burning failed, etc. Can anyone help me figure out what the issue is?

Thanks

---

### Post by Hedgehog1 on 2011-03-01
One possibility:

The transfer speed of data through your system that is needed to burn DVDs is much higher. It is possible that the data rate for CDs is low enough you don't hit the limit, but you do on DVD burning.  This will cause a 'buffer underrun' error (basically the PC could not feed data to the burner fast enough).

The data you are writing from, is it on an internal hard disk? Or is it coming from a USB drive?  USB drives are fast enough for CDs, but not fast enough for DVD burning.

Again, this is one possibility...

***The Hedge***

:KS

---

### Post by fjgaude on 2011-03-01
In Brasero you can slow the write speed down and see if that works. Check the Tools menu to see what options you have. Many of the older DVDs can't handle the fast write speeds of the new burners. Slow the write down to say, 6X, and see if you get error message then.

---

### Post by Mystro256 on 2011-03-01
Well I just did a test. The only two options in the speed menu was 4x and 8x, so I set it to 4x. It worked, which is good to hear.
Although oddly enough, the speed through most of the burning process said 6x. These disc do work on 8x, I can confirm that on another computer, but perhaps it was trying to burn faster than 8x, just like how it burnt 6x instead of 4x?
Probably just an odd quirk of my system haha

Anyway, seemed to work now, thanks for your help! :)

---

