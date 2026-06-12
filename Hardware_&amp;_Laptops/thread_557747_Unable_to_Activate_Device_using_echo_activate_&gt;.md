---
title: "Unable to Activate Device using echo activate &gt; /sys/devices/..."
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by arm-c on 2007-09-23
I cannot get my sound card activated.  When I check the resource in

/sys/devices/pnp0/00:11/resources to activate.  The output of the file is:

state = disabled
io 0x530-0x537
io 0x388-0x38b
io 0x220-0x22f
irq 5
dma 1
dma 0

running sudo echo active >/sys/devices/pnp0/00:11/resources does not change the device, nor does it give me an error.

I have also used gksu to start a xterm to get a root terminal, but I run into the same problems.  I also cannot change the file using a text editor.

I have done everything I can think of the activate the resource and keep it activated even after reboots.

THANKS IN ADVANCE!!!

---

