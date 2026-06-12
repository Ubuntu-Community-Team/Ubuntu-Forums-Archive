---
title: "Duplicate icons appearing in the Disk Mounter panel applet."
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by pjbolle on 2007-09-26
I'm having a bit of trouble trying to track down the cause of this small but noticeable annoyance. Specifically, Disk Mounter is showing duplicate icons for all mountable points.

I've never been a fan of the way automount works under Linux, so I disable it and do all mounting / unmounting manually.  I have added appropriate entries (or so I'm used to; the UUID numbers in /etc/fstab are kinda new to me) for an external FW HDD, ZIP drive, and an entry for an internal SD reader on the laptop I use.

While everything works, when any device is connected previous to mounting it, a second icon appears in Disk Mounter -- that is to say that an icon representing the entry in /etc/fstab is always visible (labeled as the mount point under /media), and then another one showing raw information about the device (such as total capacity) in the tooltip appears as well. The device can be mounted via clicking on and selecting Mount in either icon, but only the newer one shows it as being mounted -- the always-visible fstab-labeled icon always says "(not mounted)". When the device is ejected and physically removed / unplugged, the second icon disappears, and the one with the fstab label remains.

Anyone know what might be causing this? I'd appreciate any nudges in the right direction...

---

