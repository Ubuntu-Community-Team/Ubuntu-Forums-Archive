---
title: "Permission denied problem"
date: 2004-10-15
forum: Hardware &amp; Laptops
---

### Post by Perfect Storm on 2004-10-15
Some of the stuff in my Soundcard wasn't detected:

[img]http://thilockdominus.freehomepage.com/images/screenshot-device_manager.jpg[/img]

At the startup some errors occured, saying something like: Hotplug pcih permission denied.

How do I fix that?

---

### Post by Perfect Storm on 2004-10-16
this is what I get when starting my computer up:

modprobe:fatal:error inserting pciehp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko):operation not permitted

modprobe:fatal:error inserting shpchp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko):operation not permitted

modprobe:fatal:error inserting pciehp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko):operation not permitted

modprobe:fatal:error inserting shpchp(/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko):operation not permitted

---

### Post by triad169 on 2004-10-16
This is mentioned in Ubuntu Bugzilla:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=1869](https://bugzilla.ubuntu.com/show_bug.cgi?id=1869)

---

### Post by Perfect Storm on 2004-10-16
Aaah, thanks!

Hope it get fix soon :)

---

