---
title: "Will motherboard accept more memory from Video Card?"
date: 2008-08-17
forum: Hardware
---

### Post by Jeztastic on 2008-08-17
I am putting together a web browsing PC for my sister. I have a Optiplex GX1 - PIII 450/512. Details here. [http://support.dell.com/support/edocs/systems/ban_gx1/specs.htm#Memory]("http://support.dell.com/support/edocs/systems/ban_gx1/specs.htm#Memory")

I have bought 786MB of RAM to max it out. I reckon it should run Ubuntu fine for her needs. 

My question is, if I add say, a 64MB video card, will the motherboard accept it, or will it put it over the memory limit? 

Many thanks,

jez

---

### Post by az on 2008-08-17
Video card ram is not the same as system ram.  The ram on your video card is only seem by the video card and not added to the system ram.

When system ram is shared between the system and the video card, that ram is not addressed by the system so you subtract that from the total system ram.  But ram on the video card itself is different.

---

### Post by Jeztastic on 2008-08-17
Excellent, thanks. So I can get a nice meaty video card to beef up the system, right?

Edit: After looking on ebay, cards with 32 - 64 MB of RAM are all using DDR SDRAM. Is that going to work with a PC100 motherboard?

---

### Post by az on 2008-08-17
> **Jeztastic said:**
> Excellent, thanks. So I can get a nice meaty video card to beef up the system, right?

Edit: After looking on ebay, cards with 32 - 64 MB of RAM are all using DDR SDRAM. Is that going to work with a PC100 motherboard?

Yes, since the ram is used by the video card and not the motherboard.

And a beefy card will not improve system performance.  A fast card will make 3D graphics faster, but overall system performance, like surfing the web for example, will not be any faster than with a low-performance video card.

---

### Post by Jeztastic on 2008-08-17
That's useful - so it may well be money wasted. Will it help with youtube or video calling ie skype?

---

### Post by az on 2008-08-17
> **Jeztastic said:**
> That's useful - so it may well be money wasted. Will it help with youtube or video calling ie skype?

No.  That's going to be choppy on a pentium 450 Mhz.

---

### Post by kr1z on 2009-01-11
The GX1 has 4 MB of AGP video memory, and one can add 4 MB more with an add-on module (if not already installed).  I installed a 128 MB nVidia GX5200 PCI card and it worked fine once I installed it in the PCI slot closest to the motherboard on the riser (it did not work well when installed in the dual PCI/ISA slot farthest from the motherboard).

---

