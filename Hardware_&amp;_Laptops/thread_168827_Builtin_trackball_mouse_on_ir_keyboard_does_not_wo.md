---
title: "Builtin trackball mouse on ir keyboard does not work"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by chrizzler on 2006-05-01
Hi folks,

busy with a HTPC project and just received my infrared usb keyboard with builtin trackball mouse. Under windows mce 2005 (on the same comp) the keyboard/mouse does work, but under ubuntu the keyboard seems to work but the mouse pointer stays in the middle of the screen and doesnt react on trackball movements. 

Before this keyboard I used a ps/2 keyboard and ps/2 mouse... who worked fine with ubuntu.

relevant part from dmesg:
...
[4294679.348000] usbcore: registered new driver hiddev
[4294679.360000] input: USB HID v1.00 Keyboard [JME Co., Ltd. USB Wireless Controller] on usb-0000:00:1c.1-1
[4294679.376000] input: USB HID v1.00 Mouse [JME Co., Ltd. USB Wireless Controller] on usb-0000:00:1c.1-1
[4294679.376000] usbcore: registered new driver usbhid
[4294679.376000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
...
[4294689.567000] mice: PS/2 mouse device common for all mice
...

relevant from xorg.conf (forgot to copy lines from xorg.conf)
But im sure (and checked) it is standard with:
- device driver "mouse"
- protocol "IMPS/2"

What I tried:
- the only dev links which seem to be relevant to a mouse on my system are /dev/psaux and /dev/input/mice .. both dont generate anything on mouse movement with cat /dev/input/mice etc.
- catting other /dev/input devices gives garbled stuff only on /dev/input/event1 > what does this mean?
- putting /dev/put/event1 as pointer to mouse device in xorg.conf gives a randomly jumping mouse, changing the protocol to PS/2 also, and an 'auto' protocol gives nothing.

An usb mouse should work right out of the box, right? Is it possible to 'reset' the mouseconfig in ubuntu?

Can someone help me out on this one?

thanx,
Chris
](*,)

---

### Post by ja1uyn on 2006-05-13
Hi,

I just bought a similar IR keyboard with trackball (JME DX-87A) and the trackball is not recognized in Ubuntu.

@Chris: you can monitor the output in the /dev/input/event*n*
...
root@ja1uyn:/dev/input# od -x /dev/input/event3
0000000 7491 4465 4338 0002 0002 0000 0010 0000
0000020 7491 4465 433e 0002 0000 0000 0000 0000
0000040 7491 4465 1df7 0003 0002 0000 fff7 ffff
0000060 7491 4465 1dfd 0003 0002 0001 fff6 ffff
0000100 7491 4465 1e02 0003 0000 0000 0000 0000
0000120 7491 4465 d977 0003 0002 0000 fffb ffff
...

If I hotplug a standard USB mouse, /dev/input/mouse*n* and /dev/input/ts*n* are installed.

The /var/log/messages has some debug info (after enabling DEBUG in /etc/hotplug/usb.agent, /etc/hotplug/hotplug.functions & /etc/hotplug/input.agent):

...
May 13 14:31:31 localhost kernel: [4321043.597000] input: [COLOR="RoyalBlue"]USB HID v1.10 Mouse [062a:0001][/COLOR] on usb-0000:00:02.1-9.1
May 13 14:31:31 localhost default.hotplug[18489]: arguments (usb) env (SUBSYSTEM=usb OLDPWD=/ DEVPATH=/devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9.2/2-9.2.1/2-9.2.1:1.1 ACTION=add MODALIAS=usb:v05AFp8005d0100dc00dsc00dp00ic03isc01ip02 PWD=/etc/hotplug UDEV_LOG=3 UDEVD_EVENT=1 SHLVL=1 DEVICE=/proc/bus/usb/002/018 INTERFACE=3/1/2 PRODUCT=5af/8005/100 TYPE=0/0/0 DEBUG=yes PHYSDEVBUS=usb SEQNUM=1203 _=/usr/bin/env)
May 13 14:31:31 localhost input.agent[18479]:      evdev: already loaded
May 13 14:31:31 localhost default.hotplug[18628]: arguments (input) env (SUBSYSTEM=input EV=7  OLDPWD=/ NAME=062a:0001 PATH=/bin:/sbin:/usr/sbin:/usr/bin ACTION=add PWD=/etc/hotplug REL=103  KEY=1f0000 0 0 0 0 0 0 0 0  UDEVD_EVENT=1 SHLVL=1 HOME=/ PHYS=usb-0000:00:02.1-9.1/input0 PRODUCT=3/62a/1/0 DEBUG=yes _=/usr/bin/env)
May 13 14:31:31 localhost default.hotplug[18489]: invoke /etc/hotplug/usb.agent ()
May 13 14:31:31 localhost default.hotplug[18628]: invoke /etc/hotplug/input.agent ()
May 13 14:31:31 localhost usb.agent[18489]: Setup usbmouse usbhid for USB product 5af/8005/100
[COLOR="Blue"]May 13 14:31:31 localhost input.agent[18628]: Setup tsdev mousedev mousedev evdev evbug for INPUT product 3/62a/1/0[/COLOR]
May 13 14:31:31 localhost usb.agent[18489]:      usbmouse: blacklisted
May 13 14:31:31 localhost input.agent[18628]:      tsdev: already loaded
May 13 14:31:31 localhost usb.agent[18489]:      usbhid: already loaded
May 13 14:31:31 localhost input.agent[18628]:      mousedev: already loaded
...

If I hotplug the IR keyboard with trackball, it looks different:
...
May 13 14:43:24 localhost kernel: [4321756.709000] usb 2-9.2.1: new low speed USB device using ehci_hcd and address 20
May 13 14:43:24 localhost kernel: [4321756.773000] input: USB HID v1.00 Keyboard [JME Co., Ltd. USB Wireless Controller] on usb-0000:00:02.1-9.2.1
May 13 14:43:24 localhost kernel: [4321756.790000] input: [COLOR="RoyalBlue"]USB HID v1.00 Mouse [JME Co., Ltd. USB Wireless Controller][/COLOR] on usb-0000:00:02.1-9.2.1
May 13 14:43:24 localhost default.hotplug[19197]: arguments (usb) env (SUBSYSTEM=usb OLDPWD=/ DEVPATH=/devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9.2/2-9.2.1 ACTION=add PWD=/etc/hotplug UDEV_LOG=3 UDEVD_EVENT=1 SHLVL=1 PHYSDEVDRIVER=usb DEBUG=yes PHYSDEVBUS=usb SEQNUM=1215 _=/usr/bin/env)
May 13 14:43:24 localhost default.hotplug[19197]: invoke /etc/hotplug/usb.agent ()
May 13 14:43:24 localhost default.hotplug[19212]: arguments (input) env (SUBSYSTEM=input EV=120003  OLDPWD=/ NAME=JME Co., Ltd. USB Wireless Controller PATH=/bin:/sbin:/usr/sbin:/usr/bin ACTION=add PWD=/etc/hotplug KEY=e080ffdf 1cfffff ffffffff fffffffe  UDEVD_EVENT=1 SHLVL=1 HOME=/ PHYS=usb-0000:00:02.1-9.2.1/input0 PRODUCT=3/5af/8005/100 LED=1f  DEBUG=yes _=/usr/bin/env)
May 13 14:43:24 localhost default.hotplug[19212]: invoke /etc/hotplug/input.agent ()
May 13 14:43:24 localhost input.agent[19212]: Setup evdev evbug for INPUT product 3/5af/8005/100
May 13 14:43:24 localhost default.hotplug[19231]: arguments (input) env (SUBSYSTEM=input EV=5  OLDPWD=/ NAME=JME Co., Ltd. USB Wireless Controller PATH=/bin:/sbin:/usr/sbin:/usr/bin ACTION=add PWD=/etc/hotplug REL=3  UDEVD_EVENT=1 SHLVL=1 HOME=/ PHYS=usb-0000:00:02.1-9.2.1/input1 PRODUCT=3/5af/8005/100 DEBUG=yes _=/usr/bin/env)
May 13 14:43:24 localhost default.hotplug[19231]: invoke /etc/hotplug/input.agent ()
May 13 14:43:24 localhost default.hotplug[19243]: arguments (usb) env (SUBSYSTEM=usb OLDPWD=/ DEVPATH=/devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9.2/2-9.2.1/2-9.2.1:1.0 ACTION=add MODALIAS=usb:v05AFp8005d0100dc00dsc00dp00ic03isc01ip01 PWD=/etc/hotplug UDEV_LOG=3 UDEVD_EVENT=1 SHLVL=1 DEVICE=/proc/bus/usb/002/020 INTERFACE=3/1/1 PRODUCT=5af/8005/100 TYPE=0/0/0 DEBUG=yes PHYSDEVBUS=usb SEQNUM=1216 _=/usr/bin/env)
May 13 14:43:24 localhost default.hotplug[19243]: invoke /etc/hotplug/usb.agent ()
May 13 14:43:24 localhost usb.agent[19243]: Setup usbkbd usbhid for USB product 5af/8005/100
May 13 14:43:24 localhost usb.agent[19243]:      usbkbd: blacklisted
May 13 14:43:24 localhost usb.agent[19243]:      usbhid: already loaded
May 13 14:43:24 localhost default.hotplug[19251]: arguments (usb) env (SUBSYSTEM=usb OLDPWD=/ DEVPATH=/devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9.2/2-9.2.1/2-9.2.1:1.1 ACTION=add MODALIAS=usb:v05AFp8005d0100dc00dsc00dp00ic03isc01ip02 PWD=/etc/hotplug UDEV_LOG=3 UDEVD_EVENT=1 SHLVL=1 DEVICE=/proc/bus/usb/002/020 INTERFACE=3/1/2 PRODUCT=5af/8005/100 TYPE=0/0/0 DEBUG=yes PHYSDEVBUS=usb SEQNUM=1218 _=/usr/bin/env)
May 13 14:43:24 localhost default.hotplug[19251]: invoke /etc/hotplug/usb.agent ()
May 13 14:43:24 localhost usb.agent[19251]: Setup usbmouse usbhid for USB product 5af/8005/100
May 13 14:43:24 localhost usb.agent[19251]:      usbmouse: blacklisted
May 13 14:43:24 localhost usb.agent[19251]:      usbhid: already loaded
May 13 14:43:24 localhost input.agent[19212]:      evdev: already loaded
May 13 14:43:24 localhost input.agent[19231]: [COLOR="Blue"]Setup evdev evbug for INPUT product 3/5af/8005/100[/COLOR]
May 13 14:43:24 localhost input.agent[19231]:      evdev: already loaded
May 13 14:43:24 localhost input.agent[19231]:      evbug: blacklisted
May 13 14:43:24 localhost default.hotplug[19365]: arguments (input) env (PHYSDEVPATH=/devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9.2/2-9.2.1/2-9.2.1:1.1 SUBSYSTEM=input OLDPWD=/ DEVPATH=/class/input/event3 MINOR=67 ACTION=add PWD=/etc/hotplug UDEV_LOG=3 MAJOR=13 UDEVD_EVENT=1 DEVNAME=/dev/input/event3 SHLVL=1 PHYSDEVDRIVER=usbhid DEBUG=yes PHYSDEVBUS=usb SEQNUM=1219 _=/usr/bin/env)
May 13 14:43:24 localhost default.hotplug[19365]: invoke /etc/hotplug/input.agent ()
May 13 14:43:24 localhost input.agent[19365]: Setup evdev evbug for INPUT product
May 13 14:43:24 localhost input.agent[19365]:      evdev: already loaded
May 13 14:43:24 localhost input.agent[19365]:      evbug: blacklisted
May 13 14:43:24 localhost default.hotplug[19309]: arguments (input) env (PHYSDEVPATH=/devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9.2/2-9.2.1/2-9.2.1:1.0 SUBSYSTEM=input OLDPWD=/ DEVPATH=/class/input/event2 MINOR=66 ACTION=add PWD=/etc/hotplug UDEV_LOG=3 MAJOR=13 UDEVD_EVENT=1 DEVNAME=/dev/input/event2 SHLVL=1 PHYSDEVDRIVER=usbhid DEBUG=yes PHYSDEVBUS=usb SEQNUM=1217 _=/usr/bin/env)
May 13 14:43:24 localhost default.hotplug[19309]: invoke /etc/hotplug/input.agent ()
May 13 14:43:24 localhost input.agent[19309]: Setup evdev evbug for INPUT product
May 13 14:43:24 localhost input.agent[19309]:      evdev: already loaded
May 13 14:43:24 localhost input.agent[19309]:      evbug: blacklisted
May 13 14:43:25 localhost input.agent[19212]:      evbug: blacklisted
...

I marked in blue the differences. In the second debug output, mousedev and tsdev are not called.  

Can someone give me a hint, how the input and usb agents of the hotplug.d install /dev/input/ts0, /dev/input/mouse0 and calls the mousedev and tsdev driver ?

best regards,
Rolf

---

### Post by chrizzler on 2006-05-13
Using parts of the following howto I managed to get the mouse pointer working but not the buttons:
[http://aaltonen.us/archive/2005/08/26/logitech-mx1000-under-ubuntu/](http://aaltonen.us/archive/2005/08/26/logitech-mx1000-under-ubuntu/)

the relevants parts are using protocol 'evdev' and looking up the 'Dev Phys' name with 'cat /proc/bus/input/devices'.. as device I used /dev/input/event1 because that was the only device which gave output when cat-ted.

sad thing is that the mouse buttons dont show up when catting any device in /dev/input .. so the problem concerning that is probably on device driver level  evdev?

do some people know the inner working of hid devices and linux? relevant urls?

grtz,
Chris

---

