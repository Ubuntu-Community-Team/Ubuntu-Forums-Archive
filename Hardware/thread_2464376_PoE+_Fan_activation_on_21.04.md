---
title: "PoE+ Fan activation on 21.04"
date: 2021-06-30
forum: Hardware
---

### Post by goarmola on 2021-06-30
Hey!I'm trying to make the PoE+ Hat fan work on Ubuntu 21.04, I found this thread [https://raspberrypi.stackexchange.com/questions/98078/poe-hat-fan-activation-on-os-other-than-raspbianbut](https://raspberrypi.stackexchange.com/questions/98078/poe-hat-fan-activation-on-os-other-than-raspbianbut) it doesn't work, I don't have "cooling_devices" in /sys/class/thermalI also tried to use the raspi-config package available for 21.04 but still nothing...It seems I'm not the only one trying to make this work.. [https://www.raspberrypi.org/forums/viewtopic.php?f=131&t=313098Thanks](https://www.raspberrypi.org/forums/viewtopic.php?f=131&t=313098Thanks)

---

### Post by Davidian1 on 2021-07-01
Hi, I'm also trying to get the fan on the PoE+ HAT to work.  I'm using 64-bit Ubuntu 20.04 obtained from here: [https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi).  What I'm seeing more or less matches what goarmola described.  I don't have cooling_device0 within /sys/class/thermal/.  The raspi-config package installs but turning the fan on through that has no effect.

I also came here after finding that thread on the raspberrypi.org forum.

---

### Post by Davidian1 on 2021-07-16
Someone found a solution: [https://www.raspberrypi.org/forums/viewtopic.php?f=131&t=313098&p=1890082#p1890082](https://www.raspberrypi.org/forums/viewtopic.php?f=131&t=313098&p=1890082#p1890082)

---

