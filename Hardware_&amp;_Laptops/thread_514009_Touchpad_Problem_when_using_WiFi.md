---
title: "Touchpad Problem when using WiFi"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by bongoard on 2007-07-31
Hello everybody,

First of all, I'm using Ubuntu 7.04 (feisty) on Compaq Presario C300 laptop. My touchpad has been working flawlessly from the beginning of the first ubuntu install. 
Currently I install broadcom 43xx firmware and manage to get the wireless working which is really awesome.
Now the problem is : after I get the wireless working, the touchpad become unstable. 
Here is the message that I get from the log :

Jul 31 16:37:02 mooks-ubuntu kernel: [  372.880000] psmouse.c: Failed to reset mouse on isa0060/serio1
Jul 31 16:37:02 mooks-ubuntu kernel: [  372.956000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:02 mooks-ubuntu kernel: [  372.956000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:02 mooks-ubuntu kernel: [  372.968000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Jul 31 16:37:02 mooks-ubuntu kernel: [  372.972000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:02 mooks-ubuntu kernel: [  372.972000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:02 mooks-ubuntu kernel: [  372.972000] psmouse.c: issuing reconnect request
Jul 31 16:37:02 mooks-ubuntu kernel: [  373.000000] input: PS/2 Generic Mouse as /class/input/input8
Jul 31 16:37:02 mooks-ubuntu kernel: [  373.000000] psmouse.c: Failed to enable mouse on isa0060/serio1
Jul 31 16:37:10 mooks-ubuntu kernel: [  381.148000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:10 mooks-ubuntu kernel: [  381.148000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:10 mooks-ubuntu kernel: [  381.152000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:10 mooks-ubuntu kernel: [  381.152000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:10 mooks-ubuntu kernel: [  381.156000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:10 mooks-ubuntu kernel: [  381.156000] psmouse.c: issuing reconnect request
Jul 31 16:37:14 mooks-ubuntu kernel: [  384.876000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Jul 31 16:37:14 mooks-ubuntu kernel: [  384.880000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:14 mooks-ubuntu kernel: [  384.880000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:14 mooks-ubuntu kernel: [  384.884000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:14 mooks-ubuntu kernel: [  384.884000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:14 mooks-ubuntu kernel: [  384.888000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:14 mooks-ubuntu kernel: [  384.888000] psmouse.c: issuing reconnect request
Jul 31 16:37:15 mooks-ubuntu kernel: [  385.900000] psmouse.c: failed to re-enable mouse on isa0060/serio1
Jul 31 16:37:15 mooks-ubuntu kernel: [  385.900000] psmouse.c: resync failed, issuing reconnect request
Jul 31 16:37:26 mooks-ubuntu kernel: [  396.884000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jul 31 16:37:26 mooks-ubuntu kernel: [  396.888000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1

it happens all the time (seems randomly). Does anyone know how to resolve this? o and by the way, I've tried both ndiswrapper and bcm43xx-fwcutter with the same result. Is it some kind of bugs?

Thank for the help

---

### Post by bl00dfeast on 2007-09-03
i have the same problem with a Lenovo 3000 N100 0689, this notebook has a Synaptics Toouchpad and an Broadcom 4311 Wifi card, this card not work even with ndiswrapper or bcm43xx (with this module work the injection and monitor mode flawless but not internet!!!! only hacking networks for use in windows :-P))
The only solution is connect an USB mouse .

---

### Post by robotsperm on 2007-10-27
Being a huge Microsoft fanboi, I never thought I would be posting for help here!  But the cube desktop and my recent torrid love affair with Window Vista has caused me to cheat with Gusty.  So this is a great chance to test the public software movement and its ability to quickly react to its users needs.

I have a Lenovo C200 8222FU with Gusty 7.10 newly loaded on it.  Same exact problem everyone seems to be having.  The mouse will act erratic and crash the system occasionally Here are the necessary log files: 

Oct 26 23:49:36 LAPTOP kernel: [ 8780.484000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Oct 26 23:49:36 LAPTOP kernel: [ 8780.484000] psmouse.c: issuing reconnect request
Oct 26 23:49:37 LAPTOP kernel: [ 8781.036000] input: PS/2 Generic Mouse as /class/input/input19
Oct 26 23:49:37 LAPTOP kernel: [ 8781.036000] psmouse.c: Failed to enable mouse on isa0060/serio1

I'm also recieving alot of these messages: 

Oct 26 23:29:37 LAPTOP NetworkManager: <debug> [1193466577.670531] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port_logicaldev_input'). 
Oct 26 23:49:36 LAPTOP NetworkManager: <debug> [1193467776.732219] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port_logicaldev_input'). 

Ok guys, let me know if you have any questions or need anything else from me.  Now I am no stranger to systems administration, but I ask that you don't post technical requests that an 'average user' wouldn't understand or be able to do.  This is my first test of Linux for personal daily use, and I am keeping a close eye on how this issue develops to 'write home about'. 

Good luck!

---

### Post by lavinog on 2007-10-28
Same problem here.
I have a bcm-4318 wifi card and I am using the fw-cutter firmware.
I am going to switch to ndiswrapper and see if this fixes it, but unfortunately I can recreate the stutter on demand so it is frustrating trying to pinpoint the cause.
I will post back if it gets fixed.

If ndiswrapper doesn't work I would then suspect my ATI driver...since moving the mouse around the screen really fast garbled my video.  :o

---

### Post by lavinog on 2007-10-28
Switching to ndiswrapper fixed my touchpad issue

---

