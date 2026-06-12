---
title: "Touchpad freezees, is glitchy, and just plain sucks"
date: 2011-02-28
forum: Hardware
---

### Post by ffixcollector on 2011-02-28
I'm having trouble with my touchpad freezing on me. While I was inspecting syslog it happened again leading me to find;```
Feb 28 10:26:54 ffixcollector-laptop kernel: [  985.902071] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
Feb 28 10:26:54 ffixcollector-laptop kernel: [  985.906143] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:26:54 ffixcollector-laptop kernel: [  985.936147] psmouse.c: TouchPad at isa0060/serio2/input0 - driver resynched.
Feb 28 10:27:26 ffixcollector-laptop kernel: [ 1017.746507] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
Feb 28 10:27:26 ffixcollector-laptop kernel: [ 1017.750580] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:27:26 ffixcollector-laptop kernel: [ 1017.787108] psmouse.c: TouchPad at isa0060/serio2/input0 - driver resynched.
Feb 28 10:28:56 ffixcollector-laptop kernel: [ 1107.733575] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
Feb 28 10:28:56 ffixcollector-laptop kernel: [ 1107.750712] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
Feb 28 10:28:56 ffixcollector-laptop kernel: [ 1107.758176] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:28:56 ffixcollector-laptop kernel: [ 1107.782163] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
Feb 28 10:28:56 ffixcollector-laptop kernel: [ 1107.786242] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:28:56 ffixcollector-laptop kernel: [ 1107.786247] psmouse.c: issuing reconnect request
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.745363] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.749343] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.753319] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.770747] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.778633] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.778636] psmouse.c: issuing reconnect request
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.745363] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.749343] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.753319] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.770747] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.778633] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 28 10:30:26 ffixcollector-laptop kernel: [ 1197.778636] psmouse.c: issuing reconnect request

```
In Xorg I found:
```
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
```
I am not using a Mac
What can i do to fix this? It seems to happen every 2 -3 minutes.

---

### Post by ffixcollector on 2011-03-04
This is pretty bad. Its been over 4 days and no replies. Does anyone have any insight into this?

---

### Post by 2GooD on 2011-08-14
> **ffixcollector said:**
> This is pretty bad. Its been over 4 days and no replies. Does anyone have any insight into this?

Did you ever solve this? 

I started getting the same problem a few days ago on boot or resume of my Thinkpad T60p, and it only goes away after multiple reboot or suspend cycles. Very annoying!

I'm suspecting a hardware issue, but FWIF I'm still on Ubuntu 10.10:

Linux zion 2.6.35-30-generic #56-Ubuntu SMP Mon Jul 11 20:00:22 UTC 2011 i686 GNU/Linux

Description:	Ubuntu 10.10
Codename:	maverick

Real Soon Now I'm upgrading to Natty... :-)

\David

---

### Post by reverendbuck on 2011-09-20
Seems to be the same on my Thinkpad Edge 11 running natty.

---

### Post by ffixcollector on 2011-10-25
No, I just chucked it up to being a defective touchpad. The thing is, it works fine in windows. So who knows    :-?

---

### Post by Flymo on 2011-11-08
This is an old problem, sadly still with us.   

Still not sure why/what/how it happens, but this ancient  Itronix GoBook 250 (P3-700, 256 RAM) with Synaptics touchpad (id: 0x8f40b1) still shows it sporadically with Lucid 10.4.3 & E17.  Even the touchscreen works, but the touchpad? :confused:

There's a fix in the forum [here]("http://ubuntuforums.org/showthread.php?t=794670") but..... 

....it relates to GRUB 1 and I have yet to translate it into something that works with the new Byzantine GRUB 2  
<sigh>

Will post again if I concoct a fix that works in GRUB 2. 

Ben

---

### Post by Flymo on 2011-11-08
....and I just found [this page]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717970") with lots of twisty little links, all different.... ;)

---

### Post by Flymo on 2011-11-08
I seem to have struck lucky with the fix in [This Link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34501/comments/47")...:)

Well, I managed a full game of Freecell in AIsleriot without problems, so it has certainly helped....;)

Apologies for the multiple posts, but today the forum just freezes when I try to edit my previous posts.
<sigh>

Ben

---

### Post by ffixcollector on 2012-10-14
Thank You I will give that a try.

---

### Post by wildmanne39 on 2012-10-14
Old thread closed.

---

