---
title: "Printing from Ubuntu 14.04 with HP Laserjet 6P"
date: 2015-11-14
forum: Hardware
---

### Post by shadowstar45304 on 2015-11-14
I'm using a HP ProBook 6545b and have it connected with a HP LaserJet 6P  the problem is that the printer is an antique and I have to use a parallel to USB adapter cable.  Is there a way to help Ubuntu recognize the USB port with a parallel adapter pluged in?

---

### Post by tgalati4 on 2015-11-14
What version of Ubuntu?

Let's assume that you have a parallel port module.  Open a terminal:

```
lsmod | grep lp
```

Unplug the USB adapter, wait 10 seconds, then plug it back in, then post:

```
dmesg | tail -40
```

Also

```
lsusb
```

Some things to try:

[http://unix.stackexchange.com/questions/62523/how-to-install-a-printer-that-is-connected-via-an-usb-to-parallel-port-adapter](http://unix.stackexchange.com/questions/62523/how-to-install-a-printer-that-is-connected-via-an-usb-to-parallel-port-adapter)

---

