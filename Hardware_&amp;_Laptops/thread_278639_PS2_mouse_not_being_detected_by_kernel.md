---
title: "PS/2 mouse not being detected by kernel"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by Psiren on 2006-10-16
I'm having a problem with my mouse not being detected properly in the Edgy beta (also had same problem with 6.06 LTS). It works fine in the USB port, but doesn't appear in /proc/bus/input/devices if it's plugged into the PS/2 port. The psmouse module is loaded, and I've tried all the various proto=x options and pci=routeirq to no avail. I'm using the 2.6.17-10-generic kernel. I really need it in the PS/2 port so I can use it with my KVM (it works fine with my other machine, running a 2.6.14.6 custom kernel). Has anyone got any suggestions?

---

### Post by JonahRowley on 2006-10-16
This doesn't happen to be an ultra-cheap Micro Innovations optical mouse, does it?  I had the same problem with that mouse, it just won't work on PS/2 on Linux, it appears.

---

### Post by Psiren on 2006-10-17
No, it's a Microsoft Optical Intellimouse Explorer, and as I said, it works fine on my other machine, and worked fine on this one too with Debian unstable before I installed Ubuntu.

---

### Post by Psiren on 2006-10-19
Cancel this one guys, looks like it's a hardware fault that just happens to have coincided with my upgrade to ubuntu. I've just tried loading the Vista installer and it doesn't recognise my mouse either unless it's in the usb port. Seems my PS/2 port has gone bang :(

---

