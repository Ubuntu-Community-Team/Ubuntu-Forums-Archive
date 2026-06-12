---
title: "Logitech MX Anywhere Mouse Comments, Anyone with MX Air Mouse?"
date: 2009-09-02
forum: Hardware
---

### Post by BastardNamban on 2009-09-02
Hi everyone. I just picked up one of those really, really new Logitech MX Anywhere wireless mice for my Inpiron 9300 laptop. I wanted to give feedback for anyone looking to get one.

I've used this mouse for about an hour now- I LOVE IT. Worked in my 8.04 setup right out of the box great- all features work EXCEPT side scrolling. Can't get that to work yet, maybe in time.

This is the mouse Slashdot was talking about last week, supposedly it works on bare glass. I'm going to tell you- IT WORKS. I have a 5mm thick blue glass computer desk- it works smooth as silk on it with no mousepad on the bare glass- it's not hype, it really does work perfectly on glass! And I got a signal about 15 ft. away too.

What amazes me most are the 2 forward/back buttons on the side of the mouse- they work flawlessly with Firefox in Ubuntu out of the box. These things are always designed for IE, and I've seen mice that keys didn't work with Firefox even in windows. This thing works great. 

Pressing the clickwheel down shades a window in Ubuntu, and the button right under the scrollwheel activates positional auto-scroll for me, or brings up the compiz desktop cube (in my case, cylinder) on the desktop.

Finally, the mouse is very comfortable as well, has a micro receiver that fits inside the mouse for travel. The scroll could be smoother.


What I want to know is, does anyone have the Logitech MX Air Mouse, and how well does it work out of the box in Ubuntu for you? I'm considering getting one of those instead. Any comments?

---

### Post by heggink on 2009-09-18
I think it's a brilliant device. Amazed to see how it's recognised. Didn't even know until I read your post. Funny to see the scroll wheel change behaviour after a click: it toggles between a very smooth scroll and like a ribbed, standard scroll. Very nice. Going to find more things it does. This thing rocks.
:guitar:

---

### Post by 3dinos on 2009-09-25
Hello,

I've got the Logitech MX Air on an Acer REVO with
Ubuntu 9.04-32, Xorg 7.4 and kernel 2.6.28-15-generic
(booting with the "pci=routeirq" option).

Unfortunately it only works just like a normal mouse,
ie. the PLAY|PAUSE and VOL (bottom) buttons do not work,
nor their gestures do (holding these buttons down while
waving the mouse should do track skipping and volume
adjusting). It does work on the air, but one would really
need these keys to hold it up and use it as a media remote..
otherwise i see little point in using a pointer on the air.

These 'media' keys don't show up under xev and evtest,
although evtest and Xorg log show some relevant info
(see below). I've also tried adding Section "InputDevice"
with Driver "evdev", Option "Device", etc. in my xorg.conf
to no avail.

I was only able to remap the BACK (top) button to middle
click (no middle button by default) using HIDPoint.

Perhaps configuring the standard mouse buttons with
gestures (eg. using easystroke) would prove the air
pointer of this mouse useful under linux, too. But
the middle button, although picked up in easystroke,
doesn't actually draw any gestures.. practically only
button3 is left as a viable gesture button, limiting
options even more.

So I'm rather dissapointed, and I've seen a couple online
blog posts saying that the MX Air, specifically its air
gestures, worked in Ubuntu 8.04. I'd be glad to hear
if anyone can advice on how to enable these in 9.04.

Thanks,
Dinos


[grep Logitech /var/log/Xorg.0.log]

(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: xkb_options: "grp:shifts_toggle"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0


[$ sudo evtest /dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse]

Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x46d product 0xc525 version 0x111
Input device name: "Logitech USB Receiver"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 274 (MiddleBtn)
    Event code 275 (SideBtn)
    Event code 276 (ExtraBtn)
    Event code 277 (ForwardBtn)
    Event code 278 (BackBtn)
    Event code 279 (TaskBtn)
    Event code 280 (?)
    Event code 281 (?)
    Event code 282 (?)
    Event code 283 (?)
    Event code 284 (?)
    Event code 285 (?)
    Event code 286 (?)
    Event code 287 (?)
  Event type 2 (Relative)
    Event code 0 (X)
    Event code 1 (Y)
    Event code 6 (HWheel)
    Event code 8 (Wheel)
Testing ... (interrupt to exit)
^C

---

### Post by 3dinos on 2009-09-28
Hi,

just to update you on the above matter, where
the Logitech MX Air PLAY and VOL buttons, and
their built-in gestures, didn't work on my Revo
media-box.

Issue resolved: Basically I had to uninstall the
HIDPoint driver and the mouse fully worked,
with all buttons and gestures, both on the desk
and on the air. No Xorg or other configuration
is required, plugging-in the mouse USB dongle
gets it properly recognized and utilized (linux/X
plug-and-play amazes me again and again ;-)

Moreover, the mouse buttons can be remapped,
and additional gestures can be assigned to them,
using btnx and easystroke (respectively); both
are absolutely top-quality software, available
to install via apt-get, that can extend this mouse
functionality in linux in *inconceivable* ways..

Dinos

---

