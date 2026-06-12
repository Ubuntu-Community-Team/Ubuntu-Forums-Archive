---
title: "Multiple Monitors on a desktop"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by spamking2000 on 2007-07-06
OK... this might be a stupid question... but I've never used multiple monitors with a modern desktop before.

Last time I did was under DesqView on DOS on a 286....
Its pretty easy on my laptop to use both the laptop screen and the external monitor as seperate workspaces, but I've just never done it on a desktop.

My PC only has one AGP port. I assumed that if I stuck a PCI video card in that I'd get a signal on both, but that doesn't seem to be the case. The AGP (an nVidia MX440 64MB) is still working great, but I'm not even getting the BIOS screen through the PCI video card... a crummy old 2MB card.

What do I need to do? Assuming I can work like this, I'm okay buying another PCI video card with more memory, but I'm not sure that will work. Do I need a better AGP video card with 2 outputs?

Thanks,
spamking2000

---

### Post by BornToBeGeek on 2007-07-07
Hi,

Some motherboards do not support PCI VGA. First, try to remove the AGP card, and boot that way. If that works, then it should work with the AGP card as well. Just make sure the AGP and the PCI slot you put the VGA card in don't use the same IRQ (usually PCI #1 shares IRQ with AGP).

If you're out of luck with the PCI card, then it's very easy to get a cheap AGP card with dual output, just make sure it's the correct speed and voltage for your motherboard (1x, 2x, 4x or 8x).

---

