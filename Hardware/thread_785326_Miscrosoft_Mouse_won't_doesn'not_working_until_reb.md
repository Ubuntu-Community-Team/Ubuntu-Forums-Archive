---
title: "Miscrosoft Mouse won't doesn'not working until reboot"
date: 2008-05-07
forum: Hardware
---

### Post by fsm on 2008-05-07
I've got a Microsoft Wireless laser Mouse 6000 (with Keyboard) that will not work the first time Ubuntu is booted from a power-off.  It always requires a 2nd warm reboot to  work.

These are both plugged into the PS/2 ports.  When I boot 8.04,the keyboard always works but the mouse pointer will not move.  No amount of ctrl-alt-backspace will fix the problem.  If I 'shutdown -r now', upon reboot both work fine.  The same problem occurs whether the mouse is plugged into the USB port or the PS/2 port, even if I remove and reconnect the mouse.  I must always do a 2nd warm reboot to get things going.

The problem originally appeared in 7.10.  I did an upgrade to 8.04, and the problem was still there.  Then, I wiped and did a fresh install of 8.04...still there.

Anyone have any thoughts?

---

### Post by tturrisi on 2008-05-07
You try pressing the "detect" button on the mouse?

---

### Post by fsm on 2008-05-07
> **tturrisi said:**
> You try pressing the "detect" button on the mouse?

Yes, I tried that.  Even tried plugging/unplugging the mouse (when using the usb port)...still nothing.  

This is 100% reproduceable it seems.  Turn on computer and boot: no mouse.  Switch to tty1, shutdown -r now and restart: works.  It just won't work after a power on.  Something in the way the mouse is detected?

---

### Post by fsm on 2008-05-07
After some additional work I have discovered this:

I have my mouse configured to use the extra buttons, as per instructions here more or less (minus any xbindkeys)
[http://ubuntuforums.org/showthread.php?t=767206](http://ubuntuforums.org/showthread.php?t=767206)

So I am referencing the device event as reported by 
 cat /proc/bus/input/devices

and my xorg.conf uses:
        Option  "Device"        "/dev/input/event7"
for the "InputDevice" section

Sure enough, when I boot from a power off, my devices appear in a different order.  Ie.
[   25.700766] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.703653] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.703660] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.720978] mice: PS/2 mouse device common for all mice
[   41.002619] bttv0: registered device video1
[   41.002652] bttv0: registered device vbi0
[   41.320905] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input6

So that probably explains why the mouse isn't always working: referencing /dev/input/event7 in xorg.conf won't help if my mouse is suddenly on input6.  I have had the same problem with my bttv device (sometimes video0, other times video1, as it swaps with my webcam arbitrarily).

So the real problem is my device numbers keep changing order.
I would like input7 to *always* be my mouse, etc.

Does this make sense?  Is there any way to force my device numbers to be the same all the time, or am I missing something?

---

### Post by fsm on 2008-06-07
> **fsm said:**
> After some additional work I have discovered this:

...

Does this make sense?  Is there any way to force my device numbers to be the same all the time, or am I missing something?

For others with the same problem, see this thread:
"How to force device numbers to be constant" for the solution:
[http://ubuntuforums.org/showthread.php?t=797709](http://ubuntuforums.org/showthread.php?t=797709)

---

