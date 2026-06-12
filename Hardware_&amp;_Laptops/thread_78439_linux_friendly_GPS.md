---
title: "linux friendly GPS?"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2005-10-18
I'm hoping to find a GPS unit that I can plug into a micro-atx motherboard somehow (PCI, USB, Serial, whatever) and easily poll it for GPS coordinates.

I want to make a car PC that will easily track where I've been.  (and as a result, how far I've driven, and things like that)

All I need is the ability to access it from shell script or PHP (since I'm a newbie at everything else) and get my latitude and longitude coordinates whenever I want.

---

### Post by Harrkev on 2005-10-18
The first thing that you have to realize is that the world of hand-held GPS receivers falls into two worlds...

1) Serial
2) USB

Every older GPS and some newer ones fall into the Serial category.  All GPS receivers with a serial connection talk in at least one variation of the NMEA standard.  If you have this, you are set.  About once every second, the GPS will spit out a line of ASCII text with indicates, among other things, the current location.  NMEA data is over the serial port at 4800 baud, and is simple enough to parse with any sort of scripting language (as long as the language can read the serial port).

So, any GPS with a serial port and NMEA will work with Linux -- just make sure to get the cable to go with it.

Now, I am not sure about the GPS receivers with USB connections.  I do not have one, so I cannot comment.  If it has an internal "serial-port" under USB, then it SHOULD work, but YMMV.

---

