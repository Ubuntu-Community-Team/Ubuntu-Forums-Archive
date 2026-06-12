---
title: "Bluetooth device name blank after restart"
date: 2010-06-04
forum: Hardware
---

### Post by Hobgoblin on 2010-06-04
Hi, whenever I restart my system the "friendly name" in bluetooth preferences is blanked out.

If I try to connect to my phone (Nokia N97 mini) with the name blanked it will fail to connect.  It seems the Nokia doesn't like devices with no name.

If I set the name, either through the Bluetooth Preferences applet or with **sudo hciconfig hci0 name *systemname*** then it will work fine until I reboot.

Is there any way to make the name stick?

The same dongle worked fine on Ubuntu 9.04, the problem started with 9.10 and continues with 10.04

Thanks for looking.

---

### Post by Hobgoblin on 2010-06-04
Well I've worked around it by adding **hciconfig hci0 name *systemname*** to /etc/rc.local above the exit 0 line.

Obviously something isn't right.

I did try editing the name in /etc/bluetooth/main.conf but this had no effect.

---

