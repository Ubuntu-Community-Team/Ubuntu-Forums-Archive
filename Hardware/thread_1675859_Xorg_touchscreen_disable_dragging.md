---
title: "Xorg touchscreen disable dragging"
date: 2011-01-26
forum: Hardware
---

### Post by paha77 on 2011-01-26
I've configured an industrial "touchscreen" PC with Ubuntu 10.10 on it.

It has a USB Touchscreen called "IRTOUCH":

```
root@rendszer:~# lsusb -v -d 6615:0001
Bus 003 Device 002: ID 6615:0001 IRTOUCHSYSTEMS Co. Ltd. Touchscreen

```

I'm using the "evtouch" driver in Xorg and I was able to successfully calibrate it with a tool called "xinput_calibrator".

The only thing I cannot figure out is how to set it up to disable mouse drag and drop.  It's so embarrassing when I click on a link for example and the driver "thinks" I want to drag and drop that link.

My xorg.conf section is:

```

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event7"
    Option "DeviceName" "touchscreen"
    Option "MoveLimit" "1"
    Option "DragTimer" "1"
EndSection

```

Is it possible to disable drag and drop and how?

Thank you for your help.

---

### Post by paha77 on 2011-02-14
Problem solved, got the right driver and application from screen vendor.

---

### Post by jaxxed on 2011-03-13
> **paha77 said:**
> Problem solved, got the right driver and application from screen vendor.

You might want to mention what driver you got, and maybe give a link to the driver source.  Then others who see this thread can follow that path.

---

### Post by paha77 on 2011-03-15
> **jaxxed said:**
> You might want to mention what driver you got, and maybe give a link to the driver source.  Then others who see this thread can follow that path.

I've attached the driver.  Please notice this driver works only with the touchscreen specified in my first reply.  THIS IS NOT A GENERIC TOUCHSCREEN DRIVER.  And there could be newer versions.

---

