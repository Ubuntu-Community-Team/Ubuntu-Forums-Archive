---
title: "Force a usb bus rescan"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by nushoin on 2008-01-28
I'd like to force the system to rescan the usb bus.

Under Windows XP this is accomplished by opening the device manager, right-clicking on the usb bus and choosing 'rescan' (or right clicking the top node and choosing 'rescan for hardware changes). I don't remember exactly, being a long time since I've done that on a Windows machine...

My purpose is to e.g. remount an iPod device after I unmounted it, without having to disconnect and reconnect the usb cable.

Is there some way to accomplish that from the command line?

---

### Post by jeffus_il on 2008-01-28
You can use the command mount from the command line, it would be easier for you if you added a disk mount panel applet to your panel.

---

### Post by nushoin on 2008-01-28
Thanks!

This solution is good enough for me. 
I had to look at automounter at the first place if I had put a little more thought into it.

However if anyone knows how to do a generic usb hub rescan (not just for storage devices) I'd be grateful.

---

### Post by moore.bryan on 2008-07-15
> **nushoin said:**
> 
However if anyone knows how to do a generic usb hub rescan (not just for storage devices) I'd be grateful.
as would i... anyone?

---

