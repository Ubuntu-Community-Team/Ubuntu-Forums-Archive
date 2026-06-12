---
title: "How to turn off internal wireless card on boot"
date: 2016-10-21
forum: Hardware
---

### Post by wjbmd48 on 2016-10-21
Hi:

I'm running 16/04.1, and I've figured out that my slow b-g internal wireless card is designated wlp2s2, and i and manually turn it off with

sudo ifconfig wlp2s2 down.

but entering either:

sudo ifconfig wlp2s2 down

or simply

ifconfig wlp2s2 down

into the lx session autostart doesn't do the trick.  

is there a way to automatically turn it off on boot?

tx!

bill

---

### Post by TheFu on 2016-10-21
A few different ways

a) disable the wifi in the BIOS

b) disable the wifi using rfkill - this can be in rc.local

c) blacklist the wifi driver needed for the wifi device.  /etc/modprobe.d/ has examples.  Use **lsmod** and **lshw** to determine the driver being used.

Lots of choices. If you never want to use it, do "a".  The other 2 options are easy to redo/disable/enable on a running system - I'd use rfkill myself.

---

### Post by wjbmd48 on 2016-10-21
Duh, hadn't considered doing it in the BIOS.

OK, marked solved.

As always, you guys are the best!

Thanks,

Bill

---

