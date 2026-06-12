---
title: "Dell Latitude D600 and lm-sensors"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by wareagle on 2008-01-10
My Dell Latitude D600 has trouble with the chipset overheating.  After a while my ethernet quits working, and if I wait long enough, the whole system will freeze up, and when I turn it off and try to power it on again, the power button, num lock, scroll lock, and caps lock all blink rapidly for a couple seconds while the power LED remains lit.  The problem can be fixed if I press down on the CD-ROM connector near the I & K keys on the keyboard.

Anyway, in Windows there is a nice program called l8kfangui that lets me crank my fan all the way up to maximum power.  This helps alleviate the ethernet connectivity issues.

I am trying to do the same thing in Linux with lm-sensors, but it doesn't seem to work.  When I run sensors-detect, the only thing it finds is this:
```

Trying family 'SMSC'...   Yes
Found unknown chip with ID 0x1011
Probing for Super-I/O at 0x4e/0x4f

```

But at the end, it says "Sorry, no sensors were detected.  Either your sensors are not supported, or they are connected to an I2C or SMBus adapter that is not supported."

Any idea how I can get it to detect my fans?

(btw acpi -t shows my CPU core temperature)

---

### Post by wareagle on 2008-01-10
Never mind, found this: [http://dellfand.dinglisch.net](http://dellfand.dinglisch.net)

---

