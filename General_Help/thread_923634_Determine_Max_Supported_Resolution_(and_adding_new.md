---
title: "Determine Max Supported Resolution (and adding new monitor)"
date: 2008-09-18
forum: General Help
---

### Post by dsavitsk on 2008-09-18
I have Ubuntu running on an oldish computer.  "lspci | grep VGA" returns nVidea Corp NV11 [GeForce2 MX/MX 400] (rev a1). On startup the card reports 32MB of ram.

My current monitor is a flat panel that is 1024x768.  I would like to get a monitor with better resolution (ideally 1680x1050) but I don't know if the video card will support this.  Any hints on how to find this out?

Second, when installing a new monitor, do I need to edit the X config files before connecting it, after connecting it, or will ubuntu make the adjustments for me? Is this something that can be adjusted from the desktop?

Finally, if the video card cannot support this resolution, any suggestions on the cheapest video card that will?  All I will use this computer for is word processing and email reading, so gaming quality is not important.

Thanks.

---

### Post by TheLions on 2008-09-18
your GeForce2 MX/MX 400 suports that resoultion but possibly an 60Hz only.

About Xorg.conf, you can set it later after you connect your new monitor, picture would be over whole display but it will serve

---

### Post by dsavitsk on 2008-09-18
> **TheLions said:**
> your GeForce2 MX/MX 400 suports that resoultion but possibly an 60Hz only.

Fine for LCD?

---

### Post by TheLions on 2008-09-18
> **dsavitsk said:**
> Fine for LCD?

Sure

---

