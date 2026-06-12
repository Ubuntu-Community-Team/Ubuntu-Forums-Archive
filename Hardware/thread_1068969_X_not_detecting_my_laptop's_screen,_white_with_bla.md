---
title: "X not detecting my laptop's screen, white with black lines f8sp-x1"
date: 2009-02-13
forum: Hardware
---

### Post by lagitup on 2009-02-13
Hey all

I just installed intrepid (amd64 off the alt install cd, livecd produced this same issue) on my laptop, and when I start it up it boots nice and quick until it tries to draw the screen, at which point I get some fun black horizontal bars moving across a white background.  Anyone have ideas on how to make this work?

Thanks in advance!
~Lag

System info:
Laptop is an Asus f8sp-x1, intel core 2 2.0ghz, display adapter is a radeon hd 3650 1gb, 2gb + 1gb system ram, intel wireless module, asus bluetooth module.

---

### Post by lagitup on 2009-02-13
I tried switching the drive from "radeon" to "vesa" to no avail.  I've linked the xorg log (using vesa)

[http://pastebin.ca/1336494](http://pastebin.ca/1336494)

---

### Post by lagitup on 2009-02-13
installed the fglrx driver, set DefaultDepth in xorg.conf's screen section to 24 and everythign works fine!

---

