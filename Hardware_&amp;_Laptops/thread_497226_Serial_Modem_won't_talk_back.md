---
title: "Serial Modem won't talk back"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by frogbert on 2007-07-10
I'm having trouble figuring out if my serial modem is functioning correctly. I'm trying to get it set up on the server version of Ubuntu 7.04. Basically I've read that to test your modem you use the command:

"cl -l /dev/ttyS0"

and you should be able to manually issue at commands to the modem, and that it should respond to them.

For some reason this doesn't work with my modem(s) I've tried both my serial ports and a usb serial adaptor and no matter what I can't seem to even get them to respond to an AT.

Any ideas?

---

### Post by phidia on 2007-07-10
It's been awhile since I used it but minicom works well for communicating with modems. I'm not sure if it's still in ubuntu by default-I'm not on my desktop computer right now-but it should be installable. "minicom -s" from a terminal opens it. Hope that helps.

BTW I read your on a server-minicom  is not gui so it should work for you.

---

