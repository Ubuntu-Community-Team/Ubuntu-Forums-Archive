---
title: "Ubuntu 23.10, Raspberry Pi5, customized fan curve."
date: 2024-01-11
forum: Hardware
---

### Post by sblantipodi on 2024-01-11
Hi all,
is there a way to customize the Raspberry pi5 fan curve on ubuntu 23.10?

The fan starts at 50°C but I would like to make it start at 60°C.

Thanks

---

### Post by sblantipodi on 2024-01-12
I have seen this post here:
[https://forums.raspberrypi.com/viewtopic.php?p=2179210#p2179210](https://forums.raspberrypi.com/viewtopic.php?p=2179210#p2179210)

but it seems that ubuntu does not have the raspi-utils so I can't use this command to disable the fan driver:
[COLOR=#555555][FONT=Roboto]pinctrl FAN_PWM op dl

[/FONT][/COLOR]and then set my custom fan curve with a script.

are there some other way to do it in ubuntu?

---

### Post by sblantipodi on 2024-01-12
this example does not work 
[https://ubuntu.com/tutorials/gpio-on-raspberry-pi#5-pwm-example](https://ubuntu.com/tutorials/gpio-on-raspberry-pi#5-pwm-example)

---

### Post by sblantipodi on 2024-01-14
better infos here:
[https://forums.raspberrypi.com/viewtopic.php?p=2179210#p2179210](https://forums.raspberrypi.com/viewtopic.php?p=2179210#p2179210)

---

