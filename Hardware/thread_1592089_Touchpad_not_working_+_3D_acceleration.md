---
title: "Touchpad not working + 3D acceleration"
date: 2010-10-10
forum: Hardware
---

### Post by Bv202 on 2010-10-10
Hey,

I just installed Ubuntu 10.10 on a virtual machine. Everything seems to work, except my touchpad. Clicking works fine, but scrolling just doesn't work. 

I've tried it with a mouse, which works great. So it's just the touchpad which gives problems. Any idea how to get this work? I've got a Dell Studio 1558 laptop.

I also would like to use the effects of Compiz Fusion on my laptop. I know it likely won't run very smooth, but at least some effects would be nice. I've tried to enable visual effects, but it just searches for drivers and then gives me an error it couldn't enable the effects.

After some searching, it seems you have to enable 3D acceleration. It seems possible on Virtual Box, but I can't find anything about VmWare. Does anyone know if I can enable these and if yes, how?

Thank you

---

### Post by rajadain on 2010-10-10
I'm using an HP dm4 with the newfangled Synaptics ClickPad (tm, probably). It supports multi-touch in Windows, but just behaves erratically when multi-touched in Ubuntu (a bit like this: [http://ubuntuforums.org/showthread.php?t=1590466](http://ubuntuforums.org/showthread.php?t=1590466), but only with two fingers, not one). But that's okay, I don't need multi-touch so much.
What's bothering me is the lack of a right-click. Left-click, right-click, scrolling and even middle-click (by touching top-right corner of the clickpad) were working fine in Lucid. Three of these (left, scroll and middle) are working in Maverick too, but right-click is gone. I tried the method with the HP Mini 210 (can't find the link right now), and that just makes it slow and removes scrolling + middle click.
I've also installed gsynaptics, and the general synaptics driver (both of which were already and also there in my old Lucid). I've explored every GUI option I could find, and a lot of code options as well. I've also enabled SHMConfig as told in the Ubuntu Synaptics guide (again, sorry no link). I just want my right-click back.
Thanks for any updates.

---

