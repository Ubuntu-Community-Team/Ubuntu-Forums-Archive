---
title: "DDR pad woes."
date: 2009-01-19
forum: Hardware
---

### Post by lunarcloud on 2009-01-19
So I'm trying to get my ddr pad to work on Intrepid.

It's a straight up xbox DDR pad plugged into an XBOX style-USB to PC style USB adapter.

lsusb brings up

```
Bus 006 Device 005: ID 05ac:0220 Apple, Inc. Aluminum Keyboard
Bus 006 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 035: ID 0738:6040 Mad Catz, Inc.
Bus 005 Device 034: ID 0738:45ff Mad Catz, Inc.
Bus 005 Device 008: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 046d:c51b Logitech, Inc.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```(Odd that it shows up twice?)

and when I try to test it out in the KDE joystick settings thing, it knows what it is, but doesn't register any buttons, though hitting some buttons makes mouse events happen.

It used to work perfectly a year ago.

---

### Post by lunarcloud on 2009-01-31
I bought a new Xbox 360 Madcatz Beat pad pro mat.

It showed up as generic, so I built the kernel module adding

```
{ 0x0738, 0x4743, "Mad Catz Beat Pad Pro Xbox 360", MAP_DPAD_TO_AXES, XTYPE_XBOX360 },
```

And the only thing that happens is button 8 seems to be pressed and the port light just blinks.

---

### Post by lunarcloud on 2009-01-31
They seem to be both caused by xorg issues...


taken from [http://pingus.seul.org/~grumbel/tmp/md5/46b59180547f8ef58259b9fadb952d10-README]("http://pingus.seul.org/%7Egrumbel/tmp/md5/46b59180547f8ef58259b9fadb952d10-README")

```
[[ Xorg Trouble ]]
------------------

If you start xboxdrv and instead of having a fully working joystick,
you end up controllering the mouse that might be due to recent changes
in Xorg and its device hotplug handling. There are three workarounds:

Get the device id from hal:

 % hal-find-by-property --key 'info.product' --string 'Xbox Gamepad (userspace driver)'

Then remove the device from hal with:

 % hal-device -r $DEVICEID

Second workaround works with xinput:

 % xinput list
 % xinput set-int-prop $DEVICEID 'Device Enabled' 32 0

The former two workarounds are just temporary and have to be redone
after each start of xboxdrv, the last workaround is a permanent one:

You have to edit:

 /etc/hal/fdi/policy/preferences.fdi

And insert the following lines:

    <match key="input.product" string="Xbox Gamepad (userspace driver)">
      <remove key="input.x11_driver" />
    </match>
```T

Both fixes seem to work, but cannot get the permanent fix to work.

---

