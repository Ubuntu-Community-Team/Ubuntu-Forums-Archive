---
title: "radeon video card problem in 9.10"
date: 2010-02-18
forum: Hardware
---

### Post by velorution9 on 2010-02-18
I just installed ubuntu yesterday on a project box. I was a little worried because there's a Radeon video card, but it worked perfectly the first time on the DVI output. Then, later on, I accidentally booted up with the VGA cable connected to the motherboard video, as well as the DVI on the video card, and now I can't use the video card output, it defaults to the motherboard VGA. It is there when I type the lspci command, but it isn't detected in the display manager, and even when I reboot with just the DVI cable plugged in, it doesn't work. Can anyone tell me how to get it back to where the DVI output works?

---

### Post by taurolyon on 2010-02-18
This sounds mostly like a hardware issue...
[LIST]
[*]Try reseating your video card.
[/LIST]

[LIST]
[*]Check your motherboard's BIOS settings - there should be a setting for default video card (i.e. Onboard, PCI-E, AGP, PCI, etc.)
[/LIST]

---

### Post by velorution9 on 2010-02-18
I don't think so...as I said, it worked perfectly fine until I booted it up with the VGA cable plugged in.  I tried changing the default display in BIOS and it still won't work, plus now sometimes when I boot NEITHER display will work.  

????

---

