---
title: "How to force device numbers to be constant"
date: 2008-05-17
forum: Hardware
---

### Post by fsm on 2008-05-17
I'm having issues getting my mouse to work reliably in 8.04.  

When I boot, it sometimes shows up on input6, sometimes input7.  I would like input7 to *always* be my mouse, and need a way to force the order devices get detected.

I have my mouse configured as per instructions here ([http://ubuntuforums.org/showthread.php?t=767206](http://ubuntuforums.org/showthread.php?t=767206))

I am referencing the device event as reported by
cat /proc/bus/input/devices

and my xorg.conf uses:
Option "Device" "/dev/input/event7"
for the "InputDevice" section

When I boot from a power off, my devices appear in a different order. Ie.
[ 25.700766] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 25.703653] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 25.703660] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 25.720978] mice: PS/2 mouse device common for all mice
[ 41.002619] bttv0: registered device video1
[ 41.002652] bttv0: registered device vbi0
[ 41.320905] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input6

The mouse probably isn't always working because referencing /dev/input/event7 in xorg.conf won't help if my mouse is suddenly on input6. Similarly, my bttv device is sometimes video0, other times video1, as it swaps with my webcam arbitrarily.

Is there some way I can force my device numbers to be constant on reboots?  Perhaps this can be done via the rules.d stuff, but am unclear how to proceed.  

Thanks.

---

### Post by fsm on 2008-05-24
bump...

Anyone?


> **fsm said:**
> I'm having issues getting my mouse to work reliably in 8.04.  

When I boot, it sometimes shows up on input6, sometimes input7.  I would like input7 to *always* be my mouse, and need a way to force the order devices get detected.

I have my mouse configured as per instructions here ([http://ubuntuforums.org/showthread.php?t=767206](http://ubuntuforums.org/showthread.php?t=767206))

I am referencing the device event as reported by
cat /proc/bus/input/devices

and my xorg.conf uses:
Option "Device" "/dev/input/event7"
for the "InputDevice" section

When I boot from a power off, my devices appear in a different order. Ie.
[ 25.700766] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 25.703653] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 25.703660] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 25.720978] mice: PS/2 mouse device common for all mice
[ 41.002619] bttv0: registered device video1
[ 41.002652] bttv0: registered device vbi0
[ 41.320905] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input6

The mouse probably isn't always working because referencing /dev/input/event7 in xorg.conf won't help if my mouse is suddenly on input6. Similarly, my bttv device is sometimes video0, other times video1, as it swaps with my webcam arbitrarily.

Is there some way I can force my device numbers to be constant on reboots?  Perhaps this can be done via the rules.d stuff, but am unclear how to proceed.  

Thanks.

---

### Post by sisco311 on 2008-05-24
You can use the path-based symbolic link to the event corresponding to your mouse.
```
ls -la /dev/input/by-path | grep event | grep mouse
```In my case this command returns:
> lrwxrwxrwx 1 root root   9 2008-05-24 16:55 **pci-0000:00:0b.0-usb-0:3:1.0-event-mouse** -> ../event2In the xorg.conf I can use:
> Option "Device" "/dev/input/by-path/**pci-0000:00:0b.0-usb-0:3:1.0-event-mouse**"This symbolic link will always point to the mouse event.

---

### Post by fsm on 2008-06-07
> **sisco311 said:**
> You can use the path-based symbolic link to the event corresponding to your mouse.
```
ls -la /dev/input/by-path | grep event | grep mouse
```In my case this command returns:
In the xorg.conf I can use:
This symbolic link will always point to the mouse event.

This works!  Thanks a bunch!

---

