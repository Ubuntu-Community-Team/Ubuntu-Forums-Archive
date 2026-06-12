---
title: "toshiba fan once on won't switch off"
date: 2010-06-09
forum: Hardware
---

### Post by hollowhead on 2010-06-09
I have just upgraded my Toshiba L350 laptop to lucid.  Everything works out of the box apart form the rtl8187 wifi which is still crap.  The main problem I have is that the fan once it warms up enough it won't switch off.  I managed to solve it in 9.10 somehow by adding something to grub2 I think this since it is still there.


```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

``` 

I'd rather it was this way round but at the same time its annoying.  Any clues anyone?  Ta.

---

### Post by hollowhead on 2010-06-09
Scrub - seems to going off.  In my defence when I posted it had been on constantly for at least half an hour with just a bit of web browsing and wp.  Wifi is still a problem though I naively thought an upgrade to lucid would solve it......

---

