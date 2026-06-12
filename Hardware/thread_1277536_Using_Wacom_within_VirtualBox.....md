---
title: "Using Wacom within VirtualBox...."
date: 2009-09-28
forum: Hardware
---

### Post by ragtag on 2009-09-28
I have a bit of a tricky problem with my Wacom Intuos2. I'm running Jaunty 64bit, and WinXP 64 bit in VirtualBox 3.0.6. The wacom works fine in Jaunty (GIMP and everywhere else). It's set up using HAL, so no mess in xorg.conf.

It also works fine in VirtualBox, including pressure the first time I connect it (Devices>USB>Wacom), but if I disonnect it and try to reconnect it, it no longer works in the virtual machine. I suspect that it behaves a little different in Ubuntu the second time around, which is why the virtual machine is not picking it up, but I don't know what.

The second time I connect it, it does get disconnected from Ubuntu like it should, and the USB activity indicator light in VirtualBox lights up when I bring the pen near the tablet or draw, but it no longer moves the cursor in the virtual machine.

I'm a bit stumped on this one. Any ideas?

---

