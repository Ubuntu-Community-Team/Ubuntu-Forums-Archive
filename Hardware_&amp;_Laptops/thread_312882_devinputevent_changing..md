---
title: "/dev/input/event* changing."
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by Gully Foyle on 2006-12-05
Hi,

I'm using an eGalax touchscreen with both dapper and edgy. The kernel modules supplied (touchkitusb for dapper and usbtouchscreen for edgy) both work well, and I've been using the evtouch xorg touchscreen driver from [http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html](http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html) to calibrate the screen for X.

This basically works, however each time the machine is rebooted, the mouse and touchscreen are assigned to a different /dev/input/event* . Since my evtouch settings in xorg.conf (which point the driver to particular event0-3 files) only work with one of the events at a time, sometimes the calibration works for the touchscreen, sometimes it doesn't, and sometimes the calibration is applied to my mouse. Obviously, I can fix this by editing xorg.conf to point to the correct event after each reboot, but I'd really like to get this fixed, since editing xorg.conf isn't practical in the environment that I'm hoping to deploy this touchscreen box to. It won't have a keyboard attached most of the time!

---

### Post by chris_c28 on 2006-12-05
I'm having the same EXACT problem with my touchpad and mouse too. The touchpad and mouse randomly switches between events1/mouse1 and events0/mouse0. In order for my touchpad to work correctly, I need to restart x each time after booting up.

---

### Post by luismanolo on 2007-05-25
I'm using the guide:
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

good luck.;)

---

### Post by muczy on 2008-02-06
Kindda old thread, but look at this:
[http://gentoo-wiki.com/HOWTO_Advanced_Mouse#Option_2:_Configure_by_Name](http://gentoo-wiki.com/HOWTO_Advanced_Mouse#Option_2:_Configure_by_Name)

---

