---
title: "Better mobile gaming battery life"
date: 2008-06-28
forum: Hardware
---

### Post by Ekeluo on 2008-06-28
I have an idea (which some one else could possibly have implemented somewhere else) for longer gaming battery life on laptops. Please comment if you feel like and give a workability opinion on the whole thing.

Okay: I think that in some way, mobile graphics cards should be FPS conscious whether by hardware or driver functionality. Why? So that when on battery power, a gpu with multiple clock steppings could clock down and consume less power once a playable framerate (30, 48 or 60,...) is achieved. I think this can actually save significant amount of power compared to running at full tilt. I would prefer to play my Supreme commander at 30 fps for 3hrs than at 80fps for just 1.5, don't you think?
:grin:
P.S. Hope one of the people writing the open source drivers for DAAMiT cards will read this, hope to get a laptop with one of those soon!:)

---

### Post by sdennie on 2008-06-28
To a certain extent you can already do this by manually underclocking your video card.  However, I don't think the power savings will be much, if any.  On my video card, the difference full power and lowest power is about 3-4 watts.  If half power is 2 watts I'd be saving 2 watts but, because the rest of machine is fully powered up, the machine itself is probably running at around 40 watts (Just opening google earth pegs my machine to 40 watts) so, really you've only increased your battery time by about 5%.

---

### Post by Ekeluo on 2008-06-29
Oh dear, look at me thinking I had a brain storm of sorts. Well, it was interesting. BTW those figures are for a discrete graphics chipset right? Which one exactly? Not doubting, just want to get a view of how much power mobile graphics chipsets consume

---

### Post by sdennie on 2008-06-29
Well, laptop power savings is tricky.  A 3D game will generally peg a single CPU core and, once you've done that, your battery is going to drain incredibly fast regardless of what the GPU is doing it.

The numbers I quoted are from an nvidia 8400M GS and they are actually quoted while idle.  I'm assuming the numbers would scale to full power but didn't verify.

---

