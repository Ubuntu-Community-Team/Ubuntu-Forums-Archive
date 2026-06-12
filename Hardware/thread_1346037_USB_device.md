---
title: "USB device"
date: 2009-12-04
forum: Hardware
---

### Post by starfry on 2009-12-04
I have a USB webcam that was working. Since a recent update I now get errors showing in /var/log/messages:

Dec  4 21:44:52 tma1 kernel: [ 5616.803326] usb 8-6.3: rejected 1 configuration due to insufficient available bus power

I have tried using alternative usb configuration but I just get a different error:

root@tma1:~# echo -n 1 > /sys/bus/usb/devices/8-6.3/bConfigurationValue
Dec  4 21:46:14 tma1 kernel: [ 5698.461793] usb 8-6.3: new config #1 exceeds power limit by 10mA

If I do "lsusb -v" I can see the device has a "maxPower" of 510Ma.

There must be something in a recent kernel update that has started checking for power and refusing devices that would otherwise work (and they work in Windows too).

I am running Hardy LTS:
root@tma1:~# uname -a
Linux tma1 2.6.24-24-openvz #1 SMP Fri Sep 18 18:49:50 UTC 2009 x86_64 GNU/Linux

Any tips on how to fix would be greatly received.

---

### Post by starfry on 2009-12-07
Is there anyone that can help me with this problem? Sorry to bump but I am stuck!

---

