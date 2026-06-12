---
title: "Xbox 360 Wireless Gaming Controller - How to Connect?"
date: 2021-05-31
forum: Hardware
---

### Post by richyg on 2021-05-31
Having an absolute mare trying to get this to connect. It's the wireless controller that comes with the little USB receiver dongle. Can anyone advise please?

[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

This page seems to be out of date if I'm not mistaken. The very first command results in an error:

```
E: Unable to locate package automake1.9
E: Couldn't find any package by glob 'automake1.9'
E: Couldn't find any package by regex 'automake1.9'

```

---

### Post by Holger_Gehrke on 2021-06-01
You're right, that page is almost exactly 10 years old. AFAIK there's no need to compile the driver yourself anymore. Check whether it's installed by running 'find /lib/modules/ -iname "xpad*"'. That should show one 'xpad.ko' in the 'drivers/input/joystick/' directory of each installed kernel. I don't even own a controller like this, but the driver is there in case I ever get one ...

Holger

---

### Post by richyg on 2021-06-01
Hi and thanks for the reply.

Results:

```
$ find /lib/modules/ -iname "xpad*"
/lib/modules/5.8.0-40-generic/updates/dkms/xpad.ko
/lib/modules/5.8.0-40-generic/kernel/drivers/input/joystick/xpad.ko

```

Just to add more detail. When I connect the USB receiver the green light will come on, when I hit the "pair" button it will start flashing, then I tap the "pair" button on the controller it will also start flashing, but it never stops.

I read that this may be an issue, as in it pairs the controller but the controller light never stops flashing, however I tested this in Steam and the controller doesn't work.

I also opened jstest-gtk but it's just empty as though no controller is detected.

Thanks

---

### Post by richyg on 2021-06-02
So I realised there are two references to xpad.ko, due to my earlier tinkering no doubt. I have removed the version installed by dkms successfully, however nothing has changed and the controller is still not recognised or paring with the USB receiver :(

This is way more complicated than I had anticipated tbh. Linux gaming is really not as easy as some people like to say it is.

Would really appreciate any suggestions.

```
$ find /lib/modules/ -iname "xpad*"
/lib/modules/5.8.0-40-generic/kernel/drivers/input/joystick/xpad.ko

```

Thanks

---

### Post by Holger_Gehrke on 2021-06-02
OK, the driver exists. Now the next step is to check it if gets loaded.  'lsmod' gives you a list of all loaded kernel modules and you can use  'grep' to search just for the one you want like that:
```

lsmod|grep 'xpad'

```
You  can also take a look at any messages the kernel gives with 'dmesg'  after plugging in the receiver and after trying to pair the controller.

And actually gaming on Linux is quite easy. It's just the preparations for it that can be interesting, especially when trying to get something proprietary to play along.

Holger

---

### Post by richyg on 2021-06-03
Thanks for replying, and yes I was probably a little too harsh there, I have been gaming with keyboard and mouse already with relatively few issues to be fair. Anyway, let's see if we can get this controller issue solved.

```
$ lsmod|grep 'xpad'
xpad                   40960  0
ff_memless             20480  1 xpad

```
after connecting USB receiver I get this:

```
[  821.461005] usb 3-2.1: new full-speed USB device number 9 using xhci_hcd
[  821.617606] usb 3-2.1: New USB device found, idVendor=045e, idProduct=0291, bcdDevice= 1.07
[  821.617607] usb 3-2.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0

```

thanks

---

### Post by Holger_Gehrke on 2021-06-12
Vendor ID 045e is "Microsoft Corp.", product 0291 is "Xbox 360 Wireless Receiver for Windows" according to /usr/share/hwdata/usb.ids. What surprises me is that your device doesn't come up as an input device but as some kind of receiver. After a bit of searching I stumbled on [xow]("https://github.com/medusalix/xow"). Seems this "receiver" is actually a wlan device using proprietary firmware and protocol to communicate with the pad. The xpad kernel module seems to be useless in this specific case, being geared towards cabled controllers. xow might work, but its only available as source code and seems to be a dying project (last update of the readme on github says as much ...).

Holger

---

