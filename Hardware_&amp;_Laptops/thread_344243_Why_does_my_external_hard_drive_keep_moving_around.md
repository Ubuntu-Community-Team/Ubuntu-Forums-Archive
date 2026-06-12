---
title: "Why does my external hard drive keep moving around?"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by Quillz on 2007-01-22
My external hard drive, ever time I reboot my computer, either is located under "usbdisk" or "usbdisk-1." If it uses "usbdisk," then the swap partition uses "usbdisk-1," and vice versa. Is there a way to keep it listed as "usbdisk" every time I reboot?

---

### Post by tweedledee on 2007-01-27
> **Quillz said:**
> My external hard drive, ever time I reboot my computer, either is located under "usbdisk" or "usbdisk-1." If it uses "usbdisk," then the swap partition uses "usbdisk-1," and vice versa. Is there a way to keep it listed as "usbdisk" every time I reboot?

Potentially two ways, neither of which I am expert at, but you can research either or both further:
1. If the drive is always connected, you may be able to edit your /etc/fstab (I'm not sure where in the boot process that gets read, so it may not work).

2. Use udev.  A thorough tutorial is here: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) .  It gives examples of precisely how to control this kind of behavior, though I've never actually tried it.  There are also threads in the forums on this topic.

---

