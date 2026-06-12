---
title: "Touchpad re-activated after hibernation and suspend"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by merlinus on 2007-08-10
I have disabled the touchpad and pointing devices in the BIOS of my Compaq N600C.  This works upon initial bootup.

After suspend and/or hibernation, however, they are activated.

Help appreciated!

-merlin

---

### Post by ugm6hr on 2007-08-11
Maybe turn the Touchpad (and Guest device) off in xorg.conf as well.

This details the necessary commands to be added to the Touchpad section in /etc/X11/corg.conf:
```
man synaptics
```

I thinks it will be:
> Option "TouchpadOff" "1"
Option "GuestMouseOff" "1"

That way, even if it is on in BIOS, Ubuntu will never use it.

---

### Post by merlinus on 2007-08-11
Thanks for the tip.  I had great hopes, but..... it did not work.

I added to the relevant section of /etc/X11/xorg.conf, following instructions in man synaptics:

Option  "TouchpadOff"   "1"
Option  "GuestMouseOff"

but they were reactivated after coming out of hibernation.

:(

-merlin

---

