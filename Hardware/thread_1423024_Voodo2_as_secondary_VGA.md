---
title: "Voodo2 as secondary VGA"
date: 2010-03-06
forum: Hardware
---

### Post by Fisher on 2010-03-06
Hi, I just whant to have a bigger desktop without too much cost.
I'm currently using an old ATI all-in-wonder pci, with a 3d rageII chip, but I am not satisfied with the result, when I open videos with toten, they just close!
I have an old voodoo2 laying around here, can it be used as a secondary, stand-alone VGA card or just as a 3d complement? I think this should have better support, or am I wrong?
Thanks!

---

### Post by Fafler on 2010-03-06
It is, or it was, possible, i dont know if the drivers are even ported to 2.6. But because of the way to voodoo 2 works, it's a very slow solution. What about getting a old Matrox PCI card instead? You could probably get it for free by asking around.

---

### Post by cascade9 on 2010-03-06
> **Fisher said:**
> I have an old voodoo2 laying around here, can it be used as a secondary, stand-alone VGA card or just as a 3d complement?

Nope, voodoo2 are accelerators only. You must have a primary video card for the voodoo2. BTW, the voodoo 2 used 'glide' (not open GL) and as far as I know, glide was always a bit iffy on linux. 

No idea on why your videos are just closing, but its possible that the card is so old it just cant deal with video. 

If you dont need the feature of the all-in-wonder, get a nice, cheap nVidia 8400 GS PCI card.

---

