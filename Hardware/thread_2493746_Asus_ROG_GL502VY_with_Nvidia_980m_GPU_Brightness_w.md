---
title: "Asus ROG GL502VY with Nvidia 980m GPU Brightness wont working"
date: 2023-12-23
forum: Hardware
---

### Post by corola12fr on 2023-12-23
I recently installed Ubuntu Version 23.10.1 , my laptop is Asus ROG GL502VY with NVIDIA Geforce GTX 980m 8GB
 Issue: Brightness control is not working in any way(not in settings and nor in fn key)
brightness was worked in Debian 11.7 with default firmware but not worked on later version.
Ubuntu upper side is my color of screen not being corrupted but in Debian after connecting my HDMI cable laptop screen even in bios was getting weird.(till install windows or ubuntu 23.10.1 it fixed)
my fn key for keyboard backlight is also not working but im not so sensitive about that.
NVIDIA driver that now is installed version: 535.113.01
i didn't test for game but normal temperature in Ubuntu is higher than windows 11 and is about 48c to 51c
by the way i like Ubuntu and hope for fix it by the developers.):P:popcorn:

---

### Post by Autodave on 2023-12-26
First off, roll back the nVidia driver to 525 and see what happens.  There has been a lot of issues with the 535 driver.

---

### Post by corola12fr on 2023-12-29
Screen brightness control still not working.
The temperature of the VGA was reduced.
HDMI works fine like it before.
525 is working better but  brightness control still exists.

---

### Post by Bashing-om on 2023-12-29
corola12fr; A thought --

What Desktop environment are you in ? Wayland and Nvidia still many times just do not play nicely together.
```

ps -efly | grep Xorg

```
--- if you don't see the Xorg process you're using the Wayland compositor.

[INDENT]maybe
[/INDENT]

---

