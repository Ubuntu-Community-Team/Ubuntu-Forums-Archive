---
title: "Laptop screen plus 2 monitors"
date: 2011-12-23
forum: Hardware
---

### Post by gmidwood on 2011-12-23
Hello!

I'm looking for a bit of help getting a 3 monitor set up using Ubuntu 11.04, I have a (64-bit) DELL Latitude e6420 - [specs]("http://www.dell.com/us/enterprise/p/latitude-e6420/pd") - The graphics card is an 'Intel® HD Graphics 3000'. I can use the VGA port to add an additional monitor, but I would like to add a further monitor.

I have an HDMI port, but adding a monitor on this doesn't work. I have also borrowed a USB graphics card which I couldn't get working at all - if I booted up with this plugged in then I got nothing on the other two monitors.

Any suggestions as to how I can get this setup working? Is there a particular USB card I can use, or something else entirely that I can do?

TIA

---

### Post by lukeiamyourfather on 2011-12-23
Some graphics cards have more outputs than they can concurrently support, are you sure the laptop can support 3 screens simultaneously? If you unplug the VGA and try the HDMI by itself does it work?

---

### Post by gmidwood on 2011-12-23
Yeah it does, it seems to be one or the other. 

I can use either vga/hdmi with a usb graphics card in Windows, but I can't recreate it with Ubuntu

---

### Post by lukeiamyourfather on 2011-12-23
> **gmidwood said:**
> Yeah it does, it seems to be one or the other. 

I can use either vga/hdmi with a usb graphics card in Windows, but I can't recreate it with Ubuntu

What USB graphics device are you using? It may have Linux support.

---

### Post by gmidwood on 2011-12-23
I was using a [Videk AN2460 USB 2.0 to DVI/VGA Display Adaptor]("http://uk.insight.com/en-gb/apps/productpresentation/index.php?alert=categoryresults&product_id=CNX2494D00").
This is for my work laptop, so buying new kit to get it working is fine - I'm not specifically looking to get this particular device working, I just need to know if there's something I can purchase that will definitely work!

---

### Post by lukeiamyourfather on 2011-12-23
> **gmidwood said:**
> I was using a [Videk AN2460 USB 2.0 to DVI/VGA Display Adaptor]("http://uk.insight.com/en-gb/apps/productpresentation/index.php?alert=categoryresults&product_id=CNX2494D00").
This is for my work laptop, so buying new kit to get it working is fine - I'm not specifically looking to get this particular device working, I just need to know if there's something I can purchase that will definitely work!

Anything with a DL-195 chipset should work (might take some tweaking).

[http://libdlo.freedesktop.org/wiki/HowTo](http://libdlo.freedesktop.org/wiki/HowTo)

This one has a DL-195 chipset.

[http://www.siig.com/it-products/usb/converters/usb-2-0-to-dvi-vga-pro.html](http://www.siig.com/it-products/usb/converters/usb-2-0-to-dvi-vga-pro.html)

The one you already have might be the same chipset, but I couldn't find anything about it.

---

