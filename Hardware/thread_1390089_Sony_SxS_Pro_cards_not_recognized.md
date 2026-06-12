---
title: "Sony SxS Pro cards not recognized"
date: 2010-01-25
forum: Hardware
---

### Post by Albert25 on 2010-01-25
Currently, Linux doesn't seem to recognize the [Sony SxS]("http://b2b.sony.com/Solutions/subcategory/recordable-media/professional-media/sxs-pro-card") ExpressCards used by the XDCAM EX cameras.

They should be seen as a plain hard disk, but for some reason they are not.

I'm not sure if they have something special which would require a special driver, or if it's just that their PCI device id is unknown to Linux, so it doesn't even try to handle them as a hard disk.

Is there a chance to hack some configuration somewhere, using their PCI device id, so that Linux tries to see it as a hard drive?

It is frustrating to have a perfectly fine Ubuntu notebook with an ExpressCard slot, and not to be able to do fast transfers directly, requiring instead the use of a slow ExpressCard to USB adapter.

Has anyone else tried this?

Is there some other suitable place to go to for hardware support questions?

---

### Post by kiram9 on 2010-01-25
I also have the same problem. They also require a custom driver in windows to operate in the express card slot.

---

