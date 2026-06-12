---
title: "How To: Edgy 6.10 WiFi WPA-2 for Hermes orinoco WaveLAN/IEEE chipsets"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by IntuitiveNipple on 2007-01-19
I've just completed the process of building a set of drivers for the 2.6.17 kernel in Edgy Eft 6.10 which support WPA2 for the older Hermes I Lucent Orinoco chipsets that are now known as Agere WaveLAN/IEEE - phew!

Currently the GPL open-source driver without a binary firmware blob does not support WPA and there is no suggestion it ever will.

For many installations of this chipset its via a mini-PCI internal card which is attached to a PCMCIA interface - thus meaning that NDISwrapper is not an option to obtain WPA support either.

There are two simple steps to install the driver. **[I've documented how I did it in another thread](http://www.ubuntuforums.org/showpost.php?p=2033668&postcount=4)** so to save repeating myself I'm simply providing a link to that thread.

In that thread I've provided a download of the pre-built kernel object (.ko) driver for those of you who are impatient to just get it installed and working.

Remember to read my earlier articles in that thread for details of what I'd installed/done prior to building the WPA driver.

Later, I'll fully document how to build the driver from the sources.

---

### Post by Rick Z on 2008-02-20
thank you sir!!!  I just found a similar card and will work on it tonight!!!

---

