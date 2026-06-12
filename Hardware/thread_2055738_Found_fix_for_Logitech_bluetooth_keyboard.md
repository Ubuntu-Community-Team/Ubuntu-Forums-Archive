---
title: "Found fix for Logitech bluetooth keyboard"
date: 2012-09-10
forum: Hardware
---

### Post by unknownsoldierX on 2012-09-10
I've been having problems with Linux and my Logitech diNovo Edge bluetooth keyboard for years, and I've been reading about problems from a ton of other users.

Finally found the solution [here]("http://awesomelinux.blogspot.com/2011/10/ubuntu-logitech-dinovo-edge-bluetooth.html").

Now I no longer get asked to pair my keyboard, as if it's a device that should need to be paired.  It's such a simple fix.  Why isn't it configured like this in the first place?

Also, how do I make this permanent? The hid2hci.rules file says not to edit it because it will be overwritten by updates.

---

### Post by airdelroy on 2012-10-05
Will this be fixed in 12.10?

thanks,
Aaron

---

### Post by kaval on 2012-10-14
I just installed 12.10 and the bluetooth support seems to be going backwards.  I tried bluez and some of the other bluetooth managers and the logitech USB device is no longer detected at all.  With 12.04 it seemed much better and was improved from 11.10 needing an occasional delete and reinstall of the device.  Hopefully, this will get fixed as the new Trinity CPUs and AMD FM2 motherboards would make for a nice htpc with a Dinovo keyboard.

---

