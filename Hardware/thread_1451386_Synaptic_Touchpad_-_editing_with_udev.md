---
title: "Synaptic Touchpad - editing with udev"
date: 2010-04-10
forum: Hardware
---

### Post by Wardje on 2010-04-10
*Note: The fix can be found on [page 2](http://ubuntuforums.org/showthread.php?p=9454105#post9454105) of this thread.*

Hello,

I want to install the [WhatPulse]("http://whatpulse.org/") client on my laptop running Ubuntu 10.04. However, there seems to be an issue with the ability to grab clicks from the touchpad, as described at [http://jmrk.whatpulse.org/]("http://jmrk.whatpulse.org/"). The solution described there is one for 9.10 (or earlier) and as such not relevant anymore since a HAL has been dropped in favor of udev rules.

So, after some research I came across [this thread]("http://ubuntuforums.org/showthread.php?t=1401645") and used ```
synclient GrabEventDevice=0
``` to successfully change that setting. Successfully in the sense that doing ```
synclient -l
``` shows the line "GrabEventDevice = 1".

However, when clicking the buttons of my touchpad, the clicks still aren't registered by my touchpad. So I used the udev configuration in hopes of fixing it that way. Adding the file /etc/udev/rules.d/touchpad.rules with the following contents
```
ACTION!="add|change", GOTO="touchpad_end"
KERNEL!="event*", GOTO="touchpad_end"
ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="touchpad_end"
ENV{x11_options.GrabEventDevice}="0"
LABEL="touchpad_end"
```

Then I rebooted in hopes of seeing the effect, but using ```
synclient -l
``` doesn't even show GrabEventDevice as being set to 0. I'm not sure what I do wrong here, I don't really have any experience with udev. The part that troubles me most is that even setting the key-value from the command line doesn't seem to effect my ability to register clicks.


edit: may also prove useful: [https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20udev%20%28Ubuntu%2010.04%29](https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20udev%20%28Ubuntu%2010.04%29)

---

### Post by Wardje on 2010-04-10
bump:KS

---

### Post by Wardje on 2010-04-12
Anyone?:confused:

---

### Post by mastablasta on 2010-04-12
you are not running Ubuntu 10.04. You are running **Ubuntu 10.04 beta** that is ment for testing. so maybe you will find more support in some testing forums.

---

### Post by Ayuthia on 2010-04-12
> **Wardje said:**
> Hello,

I want to install the [WhatPulse]("http://whatpulse.org/") client on my laptop running Ubuntu 10.04. However, there seems to be an issue with the ability to grab clicks from the touchpad, as described at [http://jmrk.whatpulse.org/]("http://jmrk.whatpulse.org/"). The solution described there is one for 9.10 (or earlier) and as such not relevant anymore since a HAL has been dropped in favor of udev rules.

So, after some research I came across [this thread]("http://ubuntuforums.org/showthread.php?t=1401645") and used ```
synclient GrabEventDevice=0
``` to successfully change that setting. Successfully in the sense that doing ```
synclient -l
``` shows the line "GrabEventDevice = 1".

However, when clicking the buttons of my touchpad, the clicks still aren't registered by my touchpad. So I used the udev configuration in hopes of fixing it that way. Adding the file /etc/udev/rules.d/touchpad.rules with the following contents
```
ACTION!="add|change", GOTO="touchpad_end"
KERNEL!="event*", GOTO="touchpad_end"
ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="touchpad_end"
ENV{x11_options.GrabEventDevice}="0"
LABEL="touchpad_end"
```

Then I rebooted in hopes of seeing the effect, but using ```
synclient -l
``` doesn't even show GrabEventDevice as being set to 0. I'm not sure what I do wrong here, I don't really have any experience with udev. The part that troubles me most is that even setting the key-value from the command line doesn't seem to effect my ability to register clicks.


edit: may also prove useful: [https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20udev%20%28Ubuntu%2010.04%29](https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20udev%20%28Ubuntu%2010.04%29)

Have you tried:
```

ACTION!="add|change", GOTO="touchpad_end"
KERNEL!="event*", GOTO="touchpad_end"
ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="touchpad_end"
ENV{x11_options.SHMConfig}="on"
ENV{x11_options.GrabEventDevice}="0"
LABEL="touchpad_end"

```
It has been a while since I have configured synaptics, but I think that you need to have SHMConfig turned on but I could be wrong.

---

### Post by Wardje on 2010-05-06
Nop, still doesn't seem to do the trick.

I went into /var/log/udev to see if things got triggered. It did, but I also noticed some other events that might be relevant (might as in: I really got no clue). So I edited the udev rule to

```
ACTION!="add|change", GOTO="touchpad_end"
ENV{DEVPATH}!="/devices/platform/i8042/serio4/input/input7*", GOTO="touchpad_end"
ENV{x11_options.SHMConfig}="on"
ENV{x11_options.GrabEventDevice}="0"
LABEL="touchpad_end"

```

In hopes that would cover them all, which it did, going by /var/log/udev
```
UDEV  [1273146397.853934] add      /devices/platform/i8042/serio4/input/input7 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/platform/i8042/serio4/input/input7
SUBSYSTEM=input
PRODUCT=11/2/7/12b1
NAME="SynPS/2 Synaptics TouchPad"
PHYS="isa0060/serio4/input0"
EV==b
KEY==6420 0 7000f 0 0 0 0 0 0 0 0
ABS==11000003
MODALIAS=input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw
SEQNUM=1644
x11_options.SHMConfig=on
x11_options.GrabEventDevice=0

UDEV  [1273146397.856284] add      /devices/platform/i8042/serio4/input/input7/mouse1 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/platform/i8042/serio4/input/input7/mouse1
SUBSYSTEM=input
DEVNAME=/dev/input/mouse1
SEQNUM=1645
ID_INPUT=1
ID_INPUT_TOUCHPAD=1
ID_SERIAL=noserial
ID_PATH=platform-i8042-serio-4
x11_options.SHMConfig=on
x11_options.GrabEventDevice=0
MAJOR=13
MINOR=33
DEVLINKS=/dev/char/13:33 /dev/input/by-path/platform-i8042-serio-4-mouse

UDEV  [1273146397.856702] add      /devices/platform/i8042/serio4/input/input7/event7 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/platform/i8042/serio4/input/input7/event7
SUBSYSTEM=input
DEVNAME=/dev/input/event7
SEQNUM=1646
ID_INPUT=1
ID_INPUT_TOUCHPAD=1
ID_SERIAL=noserial
ID_PATH=platform-i8042-serio-4
DMI_VENDOR=Acer, inc.
x11_options.SHMConfig=on
x11_options.GrabEventDevice=0
MAJOR=13
MINOR=71
DEVLINKS=/dev/char/13:71 /dev/input/by-path/platform-i8042-serio-4-event-mouse

```

However, the WhatPulse program still doesn't seem to notice any clicks I make.:mad:

---

### Post by Wardje on 2010-05-11
Anyone got a clue? :O

---

### Post by Ayuthia on 2010-05-11
It looks like it is missing:
```

ENV{x11_driver}="synaptics"

```

---

### Post by Wardje on 2010-05-13
> **Ayuthia said:**
> It looks like it is missing:
```

ENV{x11_driver}="synaptics"

```

Sadly enough, that also didn't do the trick :(

---

### Post by Wardje on 2010-05-17
Bump

---

### Post by jerico.dev on 2010-06-12
bump

---

### Post by jerico.dev on 2010-06-12
see [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg769426.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg769426.html) and 

x11_options are no longer honored in Ubuntu 10.4, it seems, need to use xorg.conf mechanism to work around this

---

### Post by Wardje on 2010-06-13
Using the updated page on [http://jmrk.whatpulse.org/](http://jmrk.whatpulse.org/), it works for me at long last.

> X.org server 1.8 (or 1.7 without HAL): In /etc/X11/xorg.conf.d/  (in Ubuntu 10.04, the path is /usr/lib/X11/xorg.conf.d/), create a new file called 20-custom-touchpad-rules.conf or similar (the precise filename doesn't matter, as long as the file is in the right directory) with the following contents:

```
Section "InputClass"
    Identifier "custom touchpad configuration"
    MatchIsTouchpad "on"
    Option "GrabEventDevice" "false"
EndSection
```

[...]

Reboot, and WhatPulse should be able to register clicks on your touchpad.
Note: Tapping the touchpad does **not** generate real click events; it's the responsibility of the driver to detect taps and interpret them as clicks. Therefore, WhatPulse can't register clicks that you performed by tapping, and that won't change anytime soon. (Source: [http://jmrk.whatpulse.org/](http://jmrk.whatpulse.org/))

---

