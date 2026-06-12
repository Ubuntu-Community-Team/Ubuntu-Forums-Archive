---
title: "how to identify northbridge and southbridge with lspci"
date: 2015-08-27
forum: Hardware
---

### Post by mark allyn on 2015-08-27
Hello everyone,

I have been trying to use lspci and lshw to identify the northbridge and southbridge on my HP intel core duo computer.  From Intel factsheets I know that this computer is equipped with Q33 express chipset and that the southbridge is IHC9 family.  What do I look for on lspci that shows the northbridge and the southbridge.  

More generally, how do I use these, or other, commands to draw a block diagram of the system architecture?

Thanks,
Mark Allyn

---

### Post by v3.xx on 2015-08-27
Inxi may get you there, don't know for sure, but its got lots of options.

[http://manpages.ubuntu.com/manpages/trusty/man1/inxi.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/inxi.1.html)

---

### Post by tgalati4 on 2015-08-28
A simple search of [http://images.google.com](http://images.google.com) for I*ntel Q33 Express chipset block diagram* brings up a lot of pictures of block diagrams.  The linux tools for listing the PCI bus (*lspci*) shows the enumeration of devices on the PCI bus and *lsusb* does the same for the USB bus.  *lshw* shows an overall listing of hardware devices.  I don't see how any of these can help with a block diagram, other than listing devices that the kernel can recognize.

---

### Post by mark allyn on 2015-08-30
Good evening, tgalati4 and v3.xx-

v3.xx :  Thanks for the tip on inxi.  I will investigate further.

tgalati4:  Yes, there are plenty of block diagrams available from Intel on the southbridge.  You confirm what I have come to conclude:  namely, there is no linux command that maps devices to their block diagrams.  Of course, that may change once I have a look at inxi.

Too bad. 

Mark

---

