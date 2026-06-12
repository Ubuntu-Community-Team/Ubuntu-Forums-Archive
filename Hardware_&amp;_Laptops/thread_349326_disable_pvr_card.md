---
title: "disable pvr card"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by mgame2k on 2007-01-30
I would like to uninstall the or at least tell linux to uninstall the piece of hardware so that I can install the proper drivers myself.

So basically I want to disable the card entirely and redo it myself.
Edit/Delete Message

---

### Post by florizs on 2007-01-30
I don't know what kind of card you have but you could unload the kernel module by typing sudo rmmod <modulename> this removes the kernel module from the kernel. this is a dangerous thing to do learn more about it. or post more info about your situation here.

---

### Post by mgame2k on 2007-01-30
Oh I'm so sorry I completely forgot to include that info.

I have a PVR 150 PCI tv tuner card.

Ubuntu 6.10 didn't install the proper IVTV drivers so that Mythtv could work.

I'd rather redo it myself without having to remove the device and reinstalling the OS.

I just spent the weekend getting my Ralink drivers working properly so that I could surf the net.

Let me know if you need to know more about my system.

---

### Post by florizs on 2007-01-31
well if you type lsmod you can see the drivers your kernel has loaded you could post that here
after that you can remove the modules with rmmod <modulename>.

---

