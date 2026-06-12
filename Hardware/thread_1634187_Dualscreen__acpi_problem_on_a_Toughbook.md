---
title: "Dualscreen / acpi problem on a Toughbook"
date: 2010-11-30
forum: Hardware
---

### Post by aruquack on 2010-11-30
I have a Toughbook CF-28 (old 1 GHz Laptop) with a lightweight Ubuntu 10.04 (LXDM,  Enlightenment desktop environment) on it. Everything runs fine when I disable acpi in grub, except that I can't see the battery status and the only way to turn it off is via the terminal. So I would like to leave acpi on, but when I do so I get multiple problems with the screen(s). 
First, right after I boot up, with no monitor plugged in the vga out, just the internal one, the whole interface is moved slightly to the right and the things which should be on the far right side are the first on the left side. This is only the interface, the mouse cursor doesn't spring to the left side when I get too far on the right, it behaves as it should. I can get rid off that if I change with xrandr from 1024x768 to 800x600 and back. But at this point, the whole system freezes about every 15sec for a tiny moment. The vga monitor is turned off in xrandr and in bios. If one is plugged in, it doesn't freeze and it doesn't move the interface.

So I guess my question is, since I only use the internal monitor, can I hide the vga-out from Ubuntu? That might solve the problems.

---

