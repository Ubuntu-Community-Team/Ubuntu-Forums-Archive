---
title: "Logitech mouse G400 polling rate"
date: 2014-07-14
forum: Hardware
---

### Post by kakila on 2014-07-14
Hi all,

I have been trying this solution for reducing the polling rate fo the Logitech gaming mouse G400.

[https://wiki.archlinux.org/index.php/Mouse_Polling_Rate](https://wiki.archlinux.org/index.php/Mouse_Polling_Rate)

evhz works fine under Ubuntu 14.04 and the rate seems variable and reaches up to 1000Hz.

When I change the value of mousepoll to 8 (with modprobe tor by rebooting) I see the new value in /sys/module/usbhid/parameters/mousepoll but evhz still shows average rates that can reach 1kHz.

Does anybody knows how to set the polling rate in Ubuntu 14.04 for this mouse?

Thanks

---

### Post by mooreted on 2014-07-14
I don't know how to set the exact polling rate on my Razer mouse, but I use xinput to control the speed and acceleration of the mouse cursor:

Code:

#!/bin/sh
xinput --set-prop "Razer Razer DeathAdder" "Device Accel Constant Deceleration" 4
xinput --set-prop "Razer Razer DeathAdder" "Device Accel Velocity Scaling" 1


[http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)

---

### Post by kakila on 2014-07-14
Thanks, that is very informative.
I tried with several parameters but none seem to affect the polling rate. They do change the spped of the pointer but no the polling rate.

---

### Post by mooreted on 2014-07-14
Yeah, that is usually controlled by the official driver and so far they haven't given us official drivers for Linux. There may be an open source solution for your mouse, but I have never found one for mine.

---

### Post by kakila on 2014-07-15
Thanks,
I wrote to Logitech support. Lets see what they say. Maybe they have evolved into modern multi OS support

---

### Post by leszek.hanusz on 2015-06-10
Any news regarding the reducing of the mouse polling rate on Logitech mouses ?
It causes problems with the planetary annihilation game:

[http://steamcommunity.com/app/233250/discussions/2/618463738394063157/]("http://steamcommunity.com/app/233250/discussions/2/618463738394063157/")

---

