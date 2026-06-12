---
title: "Ubuntu doesn't recognize my USB ports."
date: 2009-06-27
forum: Hardware
---

### Post by Saxicide on 2009-06-27
I'm trying to dual-boot my PC for the first time, and I'm a pretty new Linux user.  Neither Ubuntu Jaunty or Hardy, or Kubunty Intrepid will recognize any of my USB ports; to the point where they stop receiving power (I assume, because all the lights turn off.)  Since my internet, keyboard, and mouse all require USB ports, this is a major problem.  I'm running Vista 64-bit already, and I believe the install CDs are 32-bit.

Any idea on how I can fix this?

---

### Post by Saxicide on 2009-06-27
*sigh*  I suppose this means no one has any idea how to fix this.  Oh well.  I guess I'll just be spending more time with Vista.

---

### Post by kelvin spratt on 2009-06-27
Ubuntu comes as 64bit as well.
As regards to your other problem my mouse and keyboard are both USB unfortunately i have never had a problem with any sort of compatibility with any Linux distro, 
 as a guess I would check your bios settings and make sure Usb is fully supported

---

### Post by Ayuthia on 2009-06-27
When your USB device quits working, can you go into the Terminal and check:
```
dmesg
```
My guess is that there is an interrupt issue and your USB module gets shut down.  If that is the case, it might just be a matter of adding a command in your menu.lst file to help it work (like noapic).

---

### Post by Saxicide on 2009-07-10
> **Ayuthia said:**
> When your USB device quits working, can you go into the Terminal and check:
```
dmesg
```My guess is that there is an interrupt issue and your USB module gets shut down.  If that is the case, it might just be a matter of adding a command in your menu.lst file to help it work (like noapic).That worked! I hit f6 at the splash screen, selected noapic, and I'm typing this from Ubuntu right now.  Thank you ^_^

---

