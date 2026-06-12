---
title: "graphic memory increase"
date: 2008-07-09
forum: Hardware
---

### Post by ettercap on 2008-07-09
hello every 1
i have an 8400M GS 128MB dedicated graphic card....i was told by my vendor that i can increase it to 700+MB by sharing my RAM to it.......
how do i do this. ???
i dont hav access to my bios coz i do not know the password

plz help..
thanks

---

### Post by Daelyn on 2008-07-10
> **ettercap said:**
> hello every 1
i have an 8400M GS 128MB dedicated graphic card....i was told by my vendor that i can increase it to 700+MB by sharing my RAM to it.......
how do i do this. ???
i dont hav access to my bios coz i do not know the password

plz help..
thanks


Nvidia previously had a "VideoRAM" option in the xorg to define memory allocation, although, that is with current drivers determined by the hardware.


You need access to BIOS to set RAM in there.
Or, if it is automatic when you increase the RAM present in machine. Linux can't "override" memory allocated.

---

