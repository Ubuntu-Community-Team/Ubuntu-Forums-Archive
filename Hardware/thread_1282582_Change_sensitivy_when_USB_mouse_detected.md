---
title: "Change sensitivy when USB mouse detected"
date: 2009-10-04
forum: Hardware
---

### Post by MegaJim on 2009-10-04
I'm hoping somebody will have tried this before !

I would like to use a script that changes the mouse sensitivity settings, the reason being that mouse sensitivity settings required for a USB mouse are quite different from those required for the touchpad on my laptop (Dell Inspirion 1525 if anybody cares)

Ideally this would be triggered by a USB connect/disconnect event, however it isn't much hassle to trigger it through a keyboard shortcut if that turns out to be too difficult.

Cheers!

---

### Post by PatrickVogeli on 2009-10-04
look into creating udev rules, it should help you.

---

### Post by MegaJim on 2009-10-04
Thanks for the hint about udev, I will experiment with it when I've made the sensitivity change scripts.

Small update, mouse sensitivity can be set using a script with the command

```

xset m acceleration threshold

```

see man xset /mouse for further details

---

### Post by MegaJim on 2009-10-04
My script at the moment:

```

#!/bin/bash
EXTERNAL="external"
TOUCHPAD="touchpad"

EXTERNAL_ACCELERATION=4/3
EXTERNAL_THRESHOLD=2

TOUCHPAD_ACCELERATION=2
TOUCHPAD_THRESHOLD=2

if [ "$1" = "$EXTERNAL" ]; then
	ACCELERATION=$EXTERNAL_ACCELERATION
	THRESHOLD=$EXTERNAL_THRESHOLD
elif [ "$1" = "$TOUCHPAD" ]; then
	ACCELERATION=$TOUCHPAD_ACCELERATION
	THRESHOLD=$TOUCHPAD_THRESHOLD
else
	ACCELERATION=$1
	THRESHOLD=$2
fi

xset mouse $ACCELERATION $THRESHOLD
notify-send "Mouse sensitivity changed" "acceleration $ACCELERATION, threshold $THRESHOLD" -t 3000

```

now onto udev!

---

### Post by MegaJim on 2009-10-05
So the next little drama was trying to find out the udevinfo command on ubuntu jaunty

```

udevadm info -q all -n /path/to/device/device-name

```

And then finding the path to my mouse.  The path output from messages log didn't provide me with a usable device name, it was:

```

input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input15
generic-usb 0003:0458:003A.0005: input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1d.1-2/input0

```

After some searching I found mouse devices located under

```

/dev/input/mouseX

```

However, with 3 mice to choose from I know not which to choose.  In the end I was a bit cheeky and did

```

sudo cat mouseX

```

on each mouse in turn.

Then just wiggle the mouse until garbage appears on screen, voila! I found it, and its udevinfo is:

```

P: /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input16/mouse1
N: input/mouse1
S: char/13:33
S: input/by-id/usb-Genius_Optical_Mouse-mouse
S: input/by-path/pci-0000:00:1d.1-usb-0:2:1.0-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input16/mouse1
E: MAJOR=13
E: MINOR=33
E: DEVNAME=/dev/input/mouse1
E: ID_VENDOR=Genius
E: ID_VENDOR_ENC=Genius
E: ID_VENDOR_ID=0458
E: ID_MODEL=Optical_Mouse
E: ID_MODEL_ENC=Optical\x20Mouse
E: ID_MODEL_ID=003a
E: ID_REVISION=0100
E: ID_SERIAL=Genius_Optical_Mouse
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usbhid
E: ID_CLASS=mouse
E: ID_PATH=pci-0000:00:1d.1-usb-0:2:1.0
E: DEVLINKS=/dev/char/13:33 /dev/input/by-id/usb-Genius_Optical_Mouse-mouse /dev/input/by-path/pci-0000:00:1d.1-usb-0:2:1.0-mouse

```

Now to make a rule

---

### Post by MegaJim on 2009-10-05
Ok, so I've created a pair of udev rules in /etc/udev/user.rules

```

ACTION=="add" ENV{ID_CLASS}=="mouse", RUN+="/home/james/bin/set-mouse-sensitivity.sh external"
ACTION=="remove" ENV{ID_CLASS}=="mouse", RUN+="/home/james/bin/set-mouse-sensitivity.sh touchpad"

```

The rules are being triggered properly with the correct paramaters and the logic of the script is correct (i can confirm this with debug echos), however I have two problems when the script is triggered by udev (not when I run it from a terminal).

Firstly, the notify-send command in the script doesn't work, and secondly the xset command (the whole point of the exercise) doesn't work either, despite the script running all the way through to the end.

The execute permissions of the script are u+x and I've tried using absolute file paths in the commands to no avail.

Any ideas?

---

### Post by MegaJim on 2009-10-05
So I added some more debugging abilities to my script, and this is what I get when its run by udev

```

/usr/bin/xset: unable to open display ""

libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

reached end of script

```

Anybody know a way to execute this script from another context that my user account has, or some other way to achieve this?

---

### Post by MegaJim on 2009-10-06
So I discovered the problem with xset, it needs the xauthority file for the current x server exported as a variable using

```

export XAUTHORITY=/var/lib/gdm/:0.Xauth

```

then xset works normally so I finally have a working rule which changes my mouse speed, woohoo !

The last little challenge is to try to get the notify-send working, however this is just to make the script cooler at this point :)

---

### Post by MegaJim on 2009-10-06
Success!  I needed to export DISPLAY and XAUTHORITY variables for the script to run against my x session.  The final script is below:

```

#!/bin/bash
export DISPLAY=:0.0
export XAUTHORITY=/var/lib/gdm/:0.Xauth

EXTERNAL="external"
TOUCHPAD="touchpad"

EXTERNAL_ACCELERATION=2
EXTERNAL_THRESHOLD=2

TOUCHPAD_ACCELERATION=3
TOUCHPAD_THRESHOLD=2

if [ "$1" = "$EXTERNAL" ]; then
	ACCELERATION=$EXTERNAL_ACCELERATION
	THRESHOLD=$EXTERNAL_THRESHOLD
elif [ "$1" = "$TOUCHPAD" ]; then
	ACCELERATION=$TOUCHPAD_ACCELERATION
	THRESHOLD=$TOUCHPAD_THRESHOLD
else
	ACCELERATION=$1
	THRESHOLD=$2
fi

xset -display :0.0 mouse $ACCELERATION $THRESHOLD
notify-send "Mouse sensitivity changed" "acceleration $ACCELERATION, threshold $THRESHOLD"

```

---

