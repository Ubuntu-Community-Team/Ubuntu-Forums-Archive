---
title: "mouse and USB flash problems"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by dacha on 2007-05-14
Hi

A mouse, and a USB flash disk, are 2 essential pieces of hardware in today's world. But...

In the past 4 years, I've had 3 different USB flash disks and 2 USB to IDE boxes. Not one of them has worked properly in Linux. When copying a large file, copying several files at the same time, or copying files while browsing the disk, every single flash disk crashes and needs to be unplugged and reinserted to be used again. The problem is reproducible on every kernel version as far back as the mid 2.4.x series and still occurs on 2.6.20-15, it happens on multiple distros and multiple machines, and it's Linux specific - on Windows 98, 2000, and XP all flash disks work perfectly. A dmesg log for Ubuntu 7.04 is attached.

The mouse in question is a cheap PS/2 optical wheelmouse. When clicking it multiple times, the mouse cursor starts jumping around and acting as if both buttons are being clicked, and only goes back to normal if I let the mouse stand still for several seconds. This bug caused me data loss a few times - the cursor thinks there is a click on the X button in the top-right corner of a window. The problem occurs on multiple distros and all kernel versions after around 2.6.7, so there's a regression that still hasn't been fixed in 2.6.20-15! Windows 98, 2000 and XP do not exhibit this problem. dmesg for Ubuntu 7.04 shows this:

[   65.380000] psmouse.c: bad data from KBC - bad parity
[   66.940000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[   66.952000] psmouse.c: resync failed, issuing reconnect request


I can completely understand why Linux doesn't support hardware for which manufacturers neither write drivers nor release specs - but not only are both the USB mass storage and PS/2 mouse specs open, but USB flash disks have been around for many years and PS/2 mice for decades, and both are cheap and ubiquitous. There is simply no excuse. As a programmer by profession, I would be deeply ashamed if wrote the psmouse or usb_storage kernel modules, because apparently even Microsoft can do better. While I appreciate many things about Linux, in the real world you only get one chance, and bugs like this would really become the nails in Ubuntu's coffin when Dell starts OEMing it.

What's the proper place to report these bugs? Since they are both kernel specific, should I report them upstream, and if so, where?

Thank you
dacha

---

