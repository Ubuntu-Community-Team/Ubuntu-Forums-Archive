---
title: "Inaccurate battery reading when resuming from hibernate"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by DizzyTech on 2007-03-30
On my [Compaq V5204NR](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00700119&lc=en&cc=us&dlc=en&product=3197922&query=Compaq%20V5204NR&dest_page=product), I get an inaccurate reading from my battery when resuming from hibernate.  All works find with standby, if it matters.

To further elaborate, I had my computer plugged in and put it on hibernate.  Later, I unplugged it and restarted my Ubuntu.  After resuming GNOME, I was immediately given a "Power Extremely Low" error.  A check of the battery icon gives me "Laptop battery 9 minutes remaining (100%)."

Running "sudo acpi -V" told me no power remaining reading, and still does not.

It's worth noting that it also told me "Thermal 1" is "ok, 60.0 degrees C".  That's about 140 degrees fahrenheit.  It'd be burning a hole in my leg if it was accurate.

A few minutes later, at 97%, it tells me I have one minute remaining and autonymously shuts down.  I restart, and it tells me 97% again.  For a few minutes, it gives me no time remaining altogether, but then gives me a reasonably accurate reading for my power.

What I'm not sure, though, is if the the inaccuracy results from me:  (a) Hibernating with the AC adapter attached, and then resuming on battery power, or (b) Hibernating and resuming alone.

---

### Post by DizzyTech on 2007-03-31
Bump...

---

### Post by DizzyTech on 2007-04-03
Bump...

---

### Post by DizzyTech on 2007-04-08
Bumped...

---

