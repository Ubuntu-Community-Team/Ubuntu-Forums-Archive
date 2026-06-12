---
title: "Vaio R505, i830, can't switch between console/X"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by stringbear on 2006-04-24
So I've got Ubuntu 5.10 up and running great except for one thing. 

When using the 5.10 Live CD, I can use ctrl-alt-f1 to swap to a text console, then use ctrl-alt-f7 to swap back to X. On my installed version of 5.10, this functionality doesn't work. When I swap back to X, the screen starts going a bright white "wave" from the bottom right corner to the upper left. The laptop isn't hard locked, but I can't reset X or get a console after that.

This didn't work in Fedora Core 5 either, but it's really frustrating, as it's preventing me from being able to suspend too.

I just can't figure out why it works on the Live CD and not on my installed copy.

---

### Post by slightly72 on 2006-04-27
I've had a similar problem on a Sharp laptop, and solved it by running X in 16bpp, instead of true color (24bpp) -- it might do the trick for you. It also solved the hibernation problem. I'm a bit confused about "i830", is that the X driver you're using, or the kernel module. On my laptop, I'm using the "i810" driver in the "Device" section of xorg.conf -- this is for a Intel 82830 Graphics Controller. In turn, this module loads the "i915" kernel module. So, this advice might or might not apply to you, but it seems that we'd be using pretty similar drivers.

---

### Post by stringbear on 2006-04-27
Holy crap, thanks! That fixed everything! I can swap between console and X with no problem and hibernate. 

And I said i830 because that's the actual graphics chipset, I believe. I still use the i810 driver in my xorg.conf.

---

