---
title: "Digital Pen NewLINK/Pegasus"
date: 2010-02-14
forum: Hardware
---

### Post by sebble on 2010-02-14
I am borrowing a digital pen and wish to get it working within Linux before purchasing one myself.

The pen is named "Digital Note Taker" from NewLINK, although hardware seems to be Pegasus Technologies. The pen set has a small receiver unit that will track pen position by ultrasonic waves and the pen itself with a similar ultrasonic device and pressure sensor (and button). Unplugged, the receiver will record and store data. (No mass storage devices visible while plugged in though)

Under M$ XP after installing the Note Taker Pro software I have a tray icon and the device is immediately found, note I get no prompt or response from Windows when the software is not running although device charges. Recorded notes will be downloaded, deleted, and then mouse mode enabled by default (absolute positioning) while the software is running (with tray icon).

I have tried using wine (1.0) on Ubuntu Netbook Remix but running the software seemed to do nothing, I then removed wine (with package manager), then the menu folder, tried wine 1.2 but now had no menu item.

Will I be able to use then pen directly (without virtualbox or vmware server on my netbook)?

I have previously tried to configure a wireless tablet with no success (no mouse clicks, just position, hal config did nothing visibly..)

So far I have just detected the device with lshal -m it appears as usb_device_e20_101_0003_0003, ending in _if0, _if1, _logicaldev_input, or _if1_logicaldev_input. The output of lshal -u shows capabilities of input, input.mouse, input.tablet, and device /dev/input/event7 or 10..

I remember when testing the graphics tablet previously I could run 'xinput test' to get real-time values but this time the driver is listed as evdev. I would be very happy to just write some python or similar to parse the output of the tester and make the mouse move if there is no driver available.

Thanks a lot! I am really trying to get everything working under linux, I can program and fiddle, have got many things set up thus far, but am a complete newbie to the linux way of doing things.

---

### Post by Favux on 2010-02-17
Hi sebble,

Welcome to Ubuntu forums!

I don't know if this will help but it seems to deal with a similar situation:  [http://ubuntuforums.org/showthread.php?t=1264775](http://ubuntuforums.org/showthread.php?t=1264775)

Hope this helps.

Good luck!

---

### Post by jeppebundsgaard on 2010-11-06
Take a look at this one: [https://launchpad.net/m210](https://launchpad.net/m210).
It also works with other brands of digital pens (in fact many pens are using the pegasus hardware). I use irisnotes.
Best regards
Jeppe

---

### Post by blackest_knight on 2010-12-09
> **jeppebundsgaard said:**
> Take a look at this one: [https://launchpad.net/m210](https://launchpad.net/m210).
It also works with other brands of digital pens (in fact many pens are using the pegasus hardware). I use irisnotes.
Best regards
Jeppe

thanks for that i bought a silvercrest one for €70 it seems reasonable although it seems to like a few inches of empty space at the top of the page

---

