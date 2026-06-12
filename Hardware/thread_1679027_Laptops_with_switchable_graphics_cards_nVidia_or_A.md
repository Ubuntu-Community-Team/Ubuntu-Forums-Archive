---
title: "Laptops with switchable graphics cards: nVidia or ATI?"
date: 2011-01-31
forum: Hardware
---

### Post by asdir on 2011-01-31
Hi all,

generally I hear that it is preferable to buy nVidia-laptops due to better drivers for the GPUs.

In particular, though, this does not seem to hold for laptops with switchable graphics cards. Both sides seem to have crappy implementation.

Is there any reason I should prefer nVidia over ATI here? The particular choices would be ATI Mobility Radeon HD 5470 vs. NVIDIA GeForce 310M.

With the Radeon I am sure to be able to switch between cards (manually) with a newer kernel (>=2.6.34) as long as I use the non-proprietary driver (i.e. the community driver, which seems to be inferior), but cannot use the proprietary driver (i.e. fglrx/Catalyst, the superior one) as long as my laptop does not have a "discrete mode" in bios (for which I, anyway, would have to reboot to switch).

For the nVidia-case the information is even more fuzzy. The only sensable thing I read was this thread:
[http://ubuntuforums.org/showthread.php?t=1470822&page=6](http://ubuntuforums.org/showthread.php?t=1470822&page=6)

However, it only tells me that (for the 330M, not the 310M, but they seem to be comparable) the driver was usable, after some hacking, but not if switching worked as it should (or the "optimus"-technology, if that's a difference).

Again, my concrete question would be: **Rather buy a laptop with the nVidia 310M or with the ATI HD 5470?** The current choices are between the [HD Pavilion dm4 1100eg (german page)]("http://h41112.www4.hp.com/promo/homelaptops/de/de/product.php?id=XE136EA&experience=direct") (which I already have but can still return) and the [Lenovo Z360]("http://www.notebooksbilliger.de/notebooks/lenovo+z360+m3594ge+core+i5+4gb+ram").

However, any insight on this issue is appreciated.

---

### Post by cascade9 on 2011-02-01
Just avoid switchable graphics if at all possible, and optimus at all costs. 

Optimus is different to switchable grpahics. Switchable graphics just switches between 2 GPUs (or in the case of intel a video chip and a GPU). Optimus actually uses both at once. The nvidia chip only displays the accelerated part of the screen, which is overlaid on top of the intel video output.

---

### Post by asdir on 2011-02-02
Do you mean "avoid Optimus at all costs" or "avoid Optimus at all costs if it is part of a switchable graphics setup". According to [this]("http://ubuntuforums.org/showthread.php?t=1579444") thread, it seems that optimus works, as long as there is no second graphics/video card involved.

Edit: Nevermind, got the answer [here]("http://ubuntuforums.org/showthread.php?p=10420999#post10420999").

---

