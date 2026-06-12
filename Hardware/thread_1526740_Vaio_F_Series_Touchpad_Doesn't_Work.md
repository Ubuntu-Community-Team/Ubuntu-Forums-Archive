---
title: "Vaio F Series Touchpad Doesn't Work"
date: 2010-07-08
forum: Hardware
---

### Post by caligula2 on 2010-07-08
I own a Sony Vaio VPCF1290X with Ubuntu 10.04 64-bit, and, as the title implies, my touchpad does not work. When checking through the Xorg.0.log in /var/log, I noticed that it does say that the mouse is recognized (even though it's as a Macintosh mouse). 

Xorg.0.log:
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/inp
ut/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catcha
ll"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)

On my previous laptop, there was a button that could turn off the touchpad. While this laptop doesn't appear to have that button, what's happening seems to be similar. Does anyone have any ideas, or need more information?

---

### Post by Zip247 on 2010-07-08
I do not have much experience with this problem, But I do have a question for you.

Does the touchpad work in you boot from the live cd??

This could help you troubleshoot a hardware or software problem.

---

### Post by terry.r on 2010-07-09
I have the exact same problem on my Vaio F series (VPCF121FD).  Here is a link to the bug posted on launchpad, it hasnt gotten much traction yet [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601239](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601239)

The problem exists both on the livecd and on an installed OS.  I have also tried other distros and have the same problem, no mouse whatsoever via the touchpad.  Windows reports the touchpad as an Alps devices.

---

### Post by terry.r on 2010-07-09
I've found a fix for this.  Credit goes to this thread [http://ubuntuforums.org/showthread.php?t=1150077&highlight=vaio+series](http://ubuntuforums.org/showthread.php?t=1150077&highlight=vaio+series) Post #2


 Here's the fix:
 
 1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
 2. Run: sudo update-grub
 3. Reboot.

---

### Post by caligula2 on 2010-07-09
That worked great! Thanks Terry.r!:D

---

### Post by terry.r on 2010-07-09
I'm not sure that all the scrolling and touchpad options work, but at least this gives us a touchpad that is somewhat useful :)

---

### Post by tankjl on 2010-08-02
Had the same problem loading Lucid on my new Vaio F series and that works but give limited function, hope they can get us full functionality soon!
 
Jeff

---

### Post by archivelog on 2011-04-25
> **terry.r said:**
> I've found a fix for this.  Credit goes to this thread [http://ubuntuforums.org/showthread.php?t=1150077&highlight=vaio+series](http://ubuntuforums.org/showthread.php?t=1150077&highlight=vaio+series) Post #2


 Here's the fix:
 
 1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
 2. Run: sudo update-grub
 3. Reboot.


It worked for my VAIO VPCEA35FG. It is great to use Ubuntu even if new in this. Thanks a lot.

---

