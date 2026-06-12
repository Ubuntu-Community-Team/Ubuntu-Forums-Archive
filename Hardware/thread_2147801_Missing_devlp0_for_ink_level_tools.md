---
title: "Missing /dev/lp0 for ink level tools"
date: 2013-05-23
forum: Hardware
---

### Post by dargaud on 2013-05-23
Hello all,
I have an Epson B42WD printer and since there's no ink level LEDs on it, I need a way to see in software, otherwise I don't know what ink needs changing.
I installed mtink some time ago and it did work. But today that the ink has run out... it won't work, the reason being that there's no /dev/lp0 or /dev/usb/lp0 or /dev/usblp0.

I tested other ink level tools, namely 'ink' and 'epscutil', but they all require a raw device such as /dev/lp0. 'link -p usb' doesn't work either.

The printer is working (or was while there was still ink in it) and I can see it with lsusb.

Why is there no /dev/lp0 ? How can I get the ink level ?!?
Thanks.

---

### Post by dargaud on 2013-05-23
Hmmm, after rebooting today, there's a /dev/usb/lp0 and mtink works fine. Don't know what was going on... BTW, how do you mark a thread solved now, I don't see it in 'Thread tools' anymore.

---

