---
title: "Disabling framebuffer?"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by quietglow on 2005-11-26
Okay, I'm on a quest to try to enable suspend on my n610c--hibernate works great but is pretty slow.

I've tried a whole slew of things, and I'd like to try running without a framebuffer.

How does one disable the framebuffer? Is this somewhere is /boot/grub/menu.lst?

---

### Post by quietglow on 2005-11-28
Okay I'm pretty sure the inability to suspend on my machine is because of a framebuffer. I need to know:

1. If raedonfb (or maybe vga16fb) is being loaded at boot

2. How to disable either of them.

Thanks!

---

### Post by ranf on 2005-11-28
[QUOTE=quietglow]Okay I'm pretty sure the inability to suspend on my machine is because of a framebuffer. I need to know:

1. If raedonfb (or maybe vga16fb) is being loaded at boot
[/QUOTE]
First find out if they are loaded:
```
lsmod
```
After I upgraded my box `vesafb' is always loaded. I think that's because of usplash.
[QUOTE=quietglow]
2. How to disable either of them.
[/QUOTE]
First try if removing `splash' from the kernel parameters helps.
For a first test I'd do that in the Grub (the boot manager) menu:
- on the standard Ubuntu menu entry, you usually boot,  hit "e" to edit
- at the kernel line hit "e" again and remove splash (for me it was in the end)
- Enter
- "b" to boot

If that helps, you could change that permanently in /boot/grub/menu.lst.

---

### Post by quietglow on 2005-11-28
Thanks, I think I have the whole managing kernel mods via grub down now.

Unfortunately, this doesn't seem to solve my issue, though. I too have the vesa framebuffer by default, but taking it out (either by removing the splash option or by actually doing a v*ideo=vesafb:off *) doesn't seem to improve things. 

My comp still suspends just fine, but hangs in the waking up process with a blank screen. Its a bummer cause I'm seeing lots of other Radeon 7500 cards, which show the same problem, fixed by getting rid of the framebuffer.

---

