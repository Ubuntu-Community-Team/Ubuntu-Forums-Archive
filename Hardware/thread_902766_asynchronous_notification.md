---
title: "asynchronous notification"
date: 2008-08-27
forum: Hardware
---

### Post by Harini1111 on 2008-08-27
Hi all,

I want to get notified my user space application from kernel space whenever my USB serial device has been either added or removed(asynchronous I/O notification). 

I tried linux hotplugging via udev rules it works fine but I looking for a callback(or similar) machnaisam or Can I send an events from my USB serial driver kernel module to user space applicaion.

Thanks,
Raj

---

### Post by IntuitiveNipple on 2008-08-27
Your application should register to receive [DBUS signals](http://dbus.freedesktop.org/doc/dbus-tutorial.html) from [hald](http://people.redhat.com/davidz/hal-spec/hal-spec.html#ov_hal_linux26).

I was looking for some links to get you started but right now I'm getting a lot of time-outs on several Internet international routes so I gave up. Be aware there is a lot of out-of-date documentation around, and that many of the latest features are only found by checking the hald source packages.

The best way to discover signals and how to use them is to look at other software.

---

