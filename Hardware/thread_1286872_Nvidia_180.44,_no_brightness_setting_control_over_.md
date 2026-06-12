---
title: "Nvidia 180.44, no brightness setting control over brightness applet"
date: 2009-10-09
forum: Hardware
---

### Post by johny_ on 2009-10-09
I'm running up Jaunty, my laptop is one of the VAIO series with the Video card using the 180.44 closed driver.
I found that I can't adjust my brightness with the GNOME applet, it tells me "cannot get laptop brightness" and moving the slider does nothing.
If I use smartdimmer package in the Terminal, It just works, it does too if I launch NVIDIA settings panel and set it from there.
I did some searching and googling oo Ubuntu forums and Lauchpad bugs but despite similar issues had been found, they were related to older kernels than mine (2.6.28-15-generic)

I'm seriously thinking about filling a bug report, but seeing that it might be related to the close driver, maybe it's just widely known issue, and it's enough to wait for the next driver release from NVidia, or should I report this right away?

---

### Post by AppleBonker on 2009-10-09
Have you tried the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=1004568&highlight=sony+brightness+working)?  It worked for me on an HP laptop.  It seems to be a more widespread issue than just Sony laptops.  I am not entirely familiar with your laptop, but if it is using a Nvidia GPU, this might work for you.

---

### Post by johny_ on 2009-10-10
I've done all this, but when I launch "acpi_listen" and press a key on my keyboard,
some strange characters comes up.
I'm using an external keyboard plugged into a laptop, as the original one has some keys damaged

Can you help me how to deal with this please?

---

### Post by johny_ on 2009-10-27
> **AppleBonker said:**
> Have you tried the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=1004568&highlight=sony+brightness+working)?  It worked for me on an HP laptop.  It seems to be a more widespread issue than just Sony laptops.  I am not entirely familiar with your laptop, but if it is using a Nvidia GPU, this might work for you.
've done all this, but when I launch "acpi_listen" and press a key on my keyboard,
some strange characters comes up.
I'm using an external keyboard plugged into a laptop, as the original one has some keys damaged

Can you help me how to deal with this please?

---

### Post by AppleBonker on 2009-10-27
Does your external keyboard have brightness keys?

---

### Post by johny_ on 2009-10-28
No, it doesn't; It's a normal one from Logitech.
I wonder if the problem is related in any way to how Xorg, recognizes and switch both keyboards.
I'll try to unplug the external one and launch "acpi_listen" and type only from the original one, then I'll do the opposite and post here my result, ok?

---

