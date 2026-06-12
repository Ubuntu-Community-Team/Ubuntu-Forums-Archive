---
title: "USB to Serial Adapters and apcupsd"
date: 2008-09-02
forum: General Help
---

### Post by triplep on 2008-09-02
I've recently setup a new APC SC1000 UPS, however, my motherboard is new fangled, and has no serial port. APC includes a USB to serial cable, but when trying to connect it to a linux machine, and configure it with apcupsd, you will get no results. Since the connection is neither USB, or serial outright, apcupsd can't communicate on to the UPS.

I found the solution at [http://www.linux-usb.org/USB-guide/x356.html](http://www.linux-usb.org/USB-guide/x356.html), which I modified slightly to suit my tastes. I used the device path of /dev/usb-tty to keep the devices isolated from the other devices that live in /dev

```

if [ ! -d /dev/usb-tty ]
then
  mkdir -p /dev/usb-tty
fi

mknod /dev/usb-tty/ttyUSB0 c 188 0
mknod /dev/usb-tty/ttyUSB1 c 188 1
mknod /dev/usb-tty/ttyUSB2 c 188 2
mknod /dev/usb-tty/ttyUSB3 c 188 3
mknod /dev/usb-tty/ttyUSB4 c 188 4
mknod /dev/usb-tty/ttyUSB5 c 188 5
mknod /dev/usb-tty/ttyUSB6 c 188 6
mknod /dev/usb-tty/ttyUSB7 c 188 7
mknod /dev/usb-tty/ttyUSB8 c 188 8
mknod /dev/usb-tty/ttyUSB9 c 188 9
mknod /dev/usb-tty/ttyUSB10 c 188 10
mknod /dev/usb-tty/ttyUSB11 c 188 11
mknod /dev/usb-tty/ttyUSB12 c 188 12
mknod /dev/usb-tty/ttyUSB13 c 188 13
mknod /dev/usb-tty/ttyUSB14 c 188 14
mknod /dev/usb-tty/ttyUSB15 c 188 15


```

When you replug the USB to serial cable you will see something similar to 

```

[178959.511262] pl2303 5-2:1.0: pl2303 converter detected
[178959.511351] usb 5-2: pl2303 converter now attached to ttyUSB0

```

In /etc/apcupsd.conf you will want the following settings, in addition to the other config items:

```


UPSCABLE smart
UPSTYPE apcsmart
DEVICE /dev/usb-tty/ttyUSB0


```

Hopefully this saves others some time digging for answers.

---

