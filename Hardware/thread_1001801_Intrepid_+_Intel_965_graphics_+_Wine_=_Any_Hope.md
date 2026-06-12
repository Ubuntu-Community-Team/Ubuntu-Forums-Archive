---
title: "Intrepid + Intel 965 graphics + Wine = Any Hope?"
date: 2008-12-04
forum: Hardware
---

### Post by Atmospherian on 2008-12-04
Hello,

I am trying to get some games to run via Wine/Cedega (namely EVE Online), i am getting the dreaded:

```
wine: Unhandled exception, starting debugger...
Could not load graphics driver 'x11drv'
```

i tried running 'sudo dpkg-reconfigure xserver-xorg' to change the driver, but i get some text based config program that seems to only be interested in the keyboard setup. 

Does anyone have any experience getting Wine/Cedega to work properly?

---

### Post by Asday on 2009-01-29
Bump, same thing's happening to me, only on an HP 530 laptop.

---

### Post by amgnix on 2009-02-15
Hi,

Have the same error on a thnkpad t60. Did you find a  solution.

Thanks
A

---

### Post by solitaire on 2009-03-15
*BUMP*

Same thing with HP 550 laptop.

anyone get this to work?

---

### Post by nwadams on 2009-03-15
is ubuntu loading the intel i810 or whatever it is driver by default or are we using the vesa driver???...That might make a difference

---

### Post by solitaire on 2009-03-15
> **nwadams said:**
> is ubuntu loading the intel i810 or whatever it is driver by default or are we using the vesa driver???...That might make a difference

As far as I know it's loading Intel's own drivers. I installed then via the "http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu" repository.

---

