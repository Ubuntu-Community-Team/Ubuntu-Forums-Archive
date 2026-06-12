---
title: "Another blank screen problem..."
date: 2014-02-16
forum: Hardware
---

### Post by dreadnot on 2014-02-16
I have a Toshiba Satellite c55-a5104, and I finally to got installed, but I had to plug in the laptop via vga into my external monitor to guide me through the gui install, but after the install, I still get the same thing. I tried installing the driver from the intel website, and that didn't seem to do anything. When I go into display options, its only showing the external monitor. I tried rebooting with nomodeset and all that does it boot into command line...which wouldn't be such a problem, if I could get back to gui. Any suggestions?

---

### Post by jp734 on 2014-02-17
If you can get into the commandline, check your /var/log/xorg.0.log

Type cat /var/log/xorg.0.log |more and look for clues why it isn't working. Post what you found.

---

