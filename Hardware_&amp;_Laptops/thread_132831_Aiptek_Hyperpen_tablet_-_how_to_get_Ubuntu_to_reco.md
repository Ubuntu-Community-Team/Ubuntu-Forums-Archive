---
title: "Aiptek Hyperpen tablet - how to get Ubuntu to recognise it"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by draconid on 2006-02-19
Hi,

I'm trying to get a rather old Aiptek Hyperpen 6000 to work with Ubuntu.  It's an old COM port version rather than USB.  I believe (from a google search) that the drivers for this are xserver-xorg-input-hyperpen which are already installed.  But for some reason Ubuntu isn't picking it up.  I've had a look at Device Manager and it doesn't seem as though it's recognising that something's attached to the COM port.  As far as I can tell the tablet itself is working (the light works when attached to the keyboard port for power, and detects when the pen is close) - I'll have to search out a windows machine to test this further I suppose.

Is there anything I need to do to get my machine to recognise the fact that something is attached to the COM port?

Thanks for any help/pointers.  I spent most of yesterday afternoon searching for help but to no avail.  I'm currently borrowing my other half's WACOM tablet which works like a dream, but I'm not going to get away with that for long!

---

### Post by luopio on 2006-03-23
from the aiptek manual page:
"aiptek  is  an  Xorg  input driver for Aiptek HyperPen USB-based tablet
devices.  This driver only supports the USB protocol,  and  only  under
Linux; for RS-232C-based HyperPens, please see the "hyperpen" driver."

But you're not losing a lot.. I've had a USB hyperpen 8000U for years and I've never got it to work (and don't know if anyone has).. I think I'll buy a wacom next :(.

---

