---
title: "laptop overheating / throttling when not under load, Temperature applet?"
date: 2009-11-02
forum: Hardware
---

### Post by discord on 2009-11-02
It does not appear that I'm doing too much with my laptop but when I dmesg I see the following

[ 1990.137544] CPU1: Temperature/speed normal
[ 1990.139154] CPU1: Temperature above threshold, cpu clock throttled (total events = 497)
[ 1990.139932] CPU1: Temperature/speed normal
[ 1990.143698] CPU1: Temperature above threshold, cpu clock throttled (total events = 498)


Can someone point me to a good temperature applet for the gnome-panel so I can monitor my CPU and see when / why it is throttling down.

---

### Post by happyhessian on 2009-11-07
Working through a similar problem on my desktop right now.  It appears to be a bug, see here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453444](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453444) .  Hope they fix it soon...

---

