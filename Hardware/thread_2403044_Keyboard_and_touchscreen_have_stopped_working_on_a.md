---
title: "Keyboard and touchscreen have stopped working on an acer laptop"
date: 2018-10-06
forum: Hardware
---

### Post by mrmola on 2018-10-06
Hi, so a few days ago my touchpad stopped working. This was very frustrating for me and so I tried to fix it. The first thing I did was edit my grup file and then update grub. Unfortunately, this caused my computer to crash at the login screen. So I undid that change and then did something that I forgot specifically what it was, but it had something to do with something with and i in it. It was either something like i956 something or i2c_hid, or something along those lines. Anyway in the end by some miracle the touchpad was repaired, but then when I rebooted my keyboard and touchscreen were not working anymore. My keyboard has a device in the /dev file at /dev/input/event4, but in the xorg log it does not say it is initialized like all the others. The keyboard also works fine in recovery mode.

---

