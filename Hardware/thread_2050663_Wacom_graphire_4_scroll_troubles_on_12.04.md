---
title: "Wacom graphire 4 scroll troubles on 12.04"
date: 2012-08-31
forum: Hardware
---

### Post by intruderukr on 2012-08-31
is there a safe solution available for the lost scrolling ability after upgrading to Precise Pangolin?  I've followed the forum, and am afraid to try anything as I see some have had real problems with broken systems after rebuilding their kernal.  Can you please direct me to safe instructions? 
thanks!

---

### Post by Favux on 2012-08-31
Hi intruderukr,

I think you just need the xf86-input-wacom driver (the X driver).  If that is correct then you need the build-against-frakenserver.patch.  You can follow the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and the instructions in [post #1034]("http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034") or follow the instructions in the updated [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").

If I'm wrong and you also need to update the wacom.ko (the usb kernel driver/module) the instructions are also on the HOW TOs.

---

