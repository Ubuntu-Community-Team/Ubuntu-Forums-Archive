---
title: "How to connect my USB LCD!"
date: 2009-06-08
forum: Hardware
---

### Post by jzmdjinn on 2009-06-08
Hello, i have an new monitor LG that has a usb connector (DisplayLink) but i cant connect it on Ubuntu.
Any ideas? 
This is the Monitor: [http://www.bit-tech.net/hardware/monitors/2008/07/17/lg-flatron-l206wu/1](http://www.bit-tech.net/hardware/monitors/2008/07/17/lg-flatron-l206wu/1)

---

### Post by IcarusR on 2009-06-08
There are linux 'drivers' for this here [http://freedesktop.org/wiki/Software/libdlo]("http://freedesktop.org/wiki/Software/libdlo") together with instructions.

Use google before you post like I did !!!

---

### Post by superdx on 2009-06-27
I don't think those are drivers?

---

### Post by trautner on 2011-08-05
Hi,

I found this helpful:
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently)

using 

-cvt (for generating the modeline)
- xandr --newmode
- xandr --addmode

and, once this worked, adding the modeline in the xorg.conf file gave me the new desired resolution in the monitor preferences menu.
Please note I connect via VGA-0. If you want to use the USB maybe the previous post (wrt drivers) is helpful.

---

