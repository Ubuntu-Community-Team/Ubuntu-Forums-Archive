---
title: "Controlling your GNOME desktop with a gamepad"
date: 2009-07-08
forum: Hardware
---

### Post by afroman10496 on 2009-07-08
I have a 10-button 2-axis 1-dpad Logitech gamepad. How can I get it to simulate a mouse and keyboard on Ubuntu 9.04? Thanks:KS

---

### Post by shatterblast on 2009-07-09
While Logitech is a great brand in my opinion, everything you listed has less than half of what a keyboard normally has.  Some projects may attempt to pick up support for game controllers.  Of the two most familiar to me, which happen to be LWJGL and SDL, SDL may provide the best advantage in compatibility.  I even think it has a very small portion dedicated to integrating game controllers with a desktop environment similar to your request.  However, my information on that technology is somewhat outdated.

The other option rests with finding a hardware driver for your Logitech device then learning how to install it properly.  It seems like you want button presses to reproduce keyboard output.  Wacom is the only device type I'm familiar with that does that very well.

---

