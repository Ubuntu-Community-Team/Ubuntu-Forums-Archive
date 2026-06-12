---
title: "Touchpad not working"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by daller on 2007-09-19
Hi there,

I have a Zepto Znote 6024W where the touchpad doesn't work!

I'm running the latest update of Kubuntu 7.10.

```
lea@lea-laptop:~$ dmesg | grep "ynaptics"
[   17.124000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x92a0b1, caps: 0xa04713/0x200000
[   17.156000] input: SynPS/2 Synaptics TouchPad as /class/input/input3

```

```
lea@lea-laptop:~$ cat /var/log/Xorg.0.log | grep "ynaptics"
(**) |-->Input Device "Synaptics Touchpad"
(WW) Duplicate core pointer devices.  Removing core pointer attribute from "Synaptics Touchpad"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(--) Synaptics Touchpad touchpad found
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(--) Synaptics Touchpad touchpad found

```

Do you have any ideas about what to do?

---

### Post by cjbehm on 2007-10-27
Hi - hopefully you've already found the answer to your problem, but you may need to make sure that your /etc/X11/xorg.conf file is properly configured so that it recognizes your touchpad. Remember that file is protected. You can edit it by entering the command 'gksu gedit /etc/X11/xorg.conf' in a terminal window.

I am by no means an expert, but I can tell you what my xorg.conf file looks like for the touchpad:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
EndSection

```

Then, in your ServerLayout section make sure that you have something like this:

```

Section ServerLayout
# You'll have lines before and/or after, but make sure that you include a line like the following
# The "Synatpics Touchpad" part should match the identifier that you use
# in the InputDevice section above
        InputDevice        "Synaptics Touchpad"        "AlwaysCore"
EndSection

```

Then you can log out and back in and it should pick up the changes you made, and with luck you'll have a working touchpad.

---

### Post by Daan_SK on 2007-10-29
sorry, may be a stupid question, but i just installed Ubuntu like 12 hours ago, but where exactly can I edit Section Server Layout?

thx for having patience

---

