---
title: "How to know which driver is controling a device?"
date: 2013-10-07
forum: Hardware
---

### Post by ercarrion43 on 2013-10-07
Hello, let me comment my problem first. I was trying to configure a trust tb-3100 tablet folloing the instruction in here:

[http://forum.intilinux.com/mypaint-help-and-tips/aiptek-media-tablet-14000u-ubuntu-12-04/](http://forum.intilinux.com/mypaint-help-and-tips/aiptek-media-tablet-14000u-ubuntu-12-04/)

After modifying the xorg.conf file, each set parameters (concretely the max and min accepted pressure and the boundaries of the working region for the tablet) resulted in a weird behaviour. I decided to unistall the xserver-xorg-input-aiptek driver (supposely the one controling the table) and realized that the xserver-xorg-input-wacom driver was installed the too. Thinking about a possible conflict I uninstalled both in synaptic and rebooted. But the tablet is still working, so I wonder which driver is controlling it?

Someone can help me?. Thanks in advance.

P.D: I'm using Ubuntu 12.04

---

### Post by Favux on 2013-10-08
Hi ercarrion43,

The non-wacom tablets tend to be rebranded a lot so to identify it first find out what the kernel is calling it.  Enter the command **lsusb** in a terminal and post the line that describes a tablet.

The evdev X driver xorg.conf.d file has a tablet catch-all snippet that will pick up a graphics tablet that isn't claimed by another driver.

To answer your question Xorg.0.log in /var/log will show you which driver has claimed a device.  It is a big file so you'll want to open it in a text editor and do a find on an appropriate keyword.  Such as a driver name, or tablet, or whatever keywords lsusb generates, etc.  For some of the drivers a short cut would be running the command **xinput list** and then using the ID# identified for the pen enter **xinput list-props ID#**.

---

### Post by ercarrion43 on 2013-10-08
That's exactly what I was looking for!! thank you very much. I copy the relevant part of the "Xorg.0.log" file:

> [   997.564] (II) config/udev: Adding input device Aiptek (/dev/input/mouse2)
[   997.564] (II) No input driver specified, ignoring this device.
[   997.564] (II) This device may have been added with another device file.
[   997.564] (II) config/udev: Adding input device Aiptek (/dev/input/event6)
[   997.564] (**) Aiptek: Applying InputClass "evdev pointer catchall"
[   997.564] (**) Aiptek: Applying InputClass "evdev keyboard catchall"
[   997.564] (**) Aiptek: Applying InputClass "evdev tablet catchall"
[   997.564] (II) Using input driver 'evdev' for 'Aiptek'
[   997.564] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   997.564] (**) Aiptek: always reports core events
[   997.564] (**) evdev: Aiptek: Device: "/dev/input/event6"
[   997.564] (--) evdev: Aiptek: Vendor 0x8ca Product 0x21
[   997.564] (--) evdev: Aiptek: Found 3 mouse buttons
[   997.564] (--) evdev: Aiptek: Found scroll wheel(s)
[   997.564] (--) evdev: Aiptek: Found relative axes
[   997.564] (--) evdev: Aiptek: Found x and y relative axes
[   997.564] (--) evdev: Aiptek: Found absolute axes
[   997.564] (--) evdev: Aiptek: Found x and y absolute axes
[   997.564] (--) evdev: Aiptek: Found absolute tablet.
[   997.564] (--) evdev: Aiptek: Found keys
[   997.564] (II) evdev: Aiptek: Configuring as tablet
[   997.565] (II) evdev: Aiptek: Configuring as keyboard
[   997.565] (II) evdev: Aiptek: Adding scrollwheel support
[   997.565] (**) evdev: Aiptek: YAxisMapping: buttons 4 and 5
[   997.565] (**) evdev: Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   997.565] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input6/event6"
[   997.565] (II) XINPUT: Adding extended input device "Aiptek" (type: KEYBOARD, id 12)
[   997.565] (**) Option "xkb_rules" "evdev"
[   997.565] (**) Option "xkb_model" "pc105"
[   997.565] (**) Option "xkb_layout" "es"
[   997.565] (WW) evdev: Aiptek: touchpads, tablets and touchscreens ignore relative axes.
[   997.565] (II) evdev: Aiptek: initialized for absolute axes.
[   997.565] (**) Aiptek: (accel) keeping acceleration scheme 1
[   997.565] (**) Aiptek: (accel) acceleration profile 0
[   997.565] (**) Aiptek: (accel) acceleration factor: 2.000
[   997.565] (**) Aiptek: (accel) acceleration threshold: 4

As you said it was the evdev driver the one taking charge of the tablet. I didn't know about its existance.

Thanks again!.

---

