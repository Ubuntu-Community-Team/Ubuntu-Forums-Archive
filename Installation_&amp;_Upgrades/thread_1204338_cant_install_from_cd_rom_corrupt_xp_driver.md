---
title: "cant install from cd rom corrupt xp driver"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by jsweeny on 2009-07-04
I am having problems installing 9.04 from the cd because the driver for the cd drive seems to not be corrupt.  I can't even use this drive normally.  It keeps asking me to press F1 to retry.  Can I use my other drive to install from?  If so how do I tell my machine to boot from that drive rather than the defalt drive?

---

### Post by earthpigg on 2009-07-04
can you *boot* from the cd? if so, then the windows drivers do not matter, and you can install ubuntu that way.

if you can *not* boot from the cd, then the cd drive is probably physically broken and neither windows nor ubuntu can do anything about it.

fortunately, you do not need a working cd drive to install or use ubuntu, assuming your computer can boot from usb:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

that wiki article probably explains it better than i ever could.



edit: the _**super-easy**_ way, which i dont see prominently displayed in that wiki article, is to find a computer with a working CD drive, boot into the ubuntu live cd, and select System->Administration-> USB Startup Disk Creator.... note that it will ask you for the ubuntu .iso, so you will need to know where you have that downloaded to.

then boot from that usb disk on your target computer, and install.

---

