---
title: "Setting of screen brightness doesn't work LAPTOP"
date: 2014-08-20
forum: Hardware
---

### Post by aleks5 on 2014-08-20
[COLOR=#000000]Hi there.
I have a laptop asus x55 2e AMD on ubuntu 14.04 with graphic adapter Radeon HD 8330. On this doesn't work buttons of tune [/COLOR]screen brightness.

What I did:

I add the string with "RGUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1" into GRUB configuration file.
Then, I rebiuld GRUB and restart computer.
When I lokeed into the folder /sys/class/backlight, I saw that it is empty.

Drivers of graphic adapter was installed.

Please, help me.

Sorry for my hard English.

---

