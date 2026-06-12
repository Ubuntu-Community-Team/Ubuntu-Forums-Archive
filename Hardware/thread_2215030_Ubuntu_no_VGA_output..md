---
title: "Ubuntu no VGA output."
date: 2014-04-04
forum: Hardware
---

### Post by diverlonnie on 2014-04-04
I successfully installed 32 bit 12.04.3 on one computer and 64 bit 13.10 on another. Both had XP and were connected to a combination TV with a VGA port. Both worked fine. I packed the computers up and took them to my summer home and hooked them up to a different brand of  combination TV with a VGA port. One a Vizio the other a Polaroid. Watching the hard drive indicator both appeared to fire up fine but both monitors say no signal.

I'm at a loss.

---

### Post by TheFu on 2014-04-04
Make the PC output the resolution that the TV supports.  Need to lookup the TV resolutions - DO NOT PUSH ANY RESOLUTION HIGHER than the TV supports.

Use xrandr to set the PC resolution.  That can be difficult without a monitor to see the connection, but it is possible to ssh in, set the DISPLAY to :0 and set the resolution.

---

### Post by diverlonnie on 2014-04-04
Okay thanks. I'll wait until I can reconnect them to the setup monitor I used and reduce the resolution.

---

