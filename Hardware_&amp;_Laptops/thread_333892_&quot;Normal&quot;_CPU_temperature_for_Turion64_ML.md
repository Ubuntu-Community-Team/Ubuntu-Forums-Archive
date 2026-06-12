---
title: "&quot;Normal&quot; CPU temperature for Turion64 ML-x processors?"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by codejak on 2007-01-08
Hi all!

I just recently installed Edgy on my HP Compaq nx6125. By chance I ran into the overheating issue without ever realizing it in the first couple of days of running the system. When actively monitoring CPU temperature though, I noticed that my machine regularly went into the 70s (celsius) and even up to 80°C within minutes after booting up.

I now added "noacpi nolapic" to the kernel options and the problem appears to have been resolved, as I am now usually below 60°C. (I am using the GNOME Sensors applet for monitoring.) Thanks to Patsoe for the excellent description [to be found here]("http://ubuntuforums.org/showthread.php?t=189337").

Still, I would like to know what operating temperature for an AMD Turion 64-bit processor should be expected as "normal," given that my roughly 50°C - 60°C during simple operations (browsing, listening to music, e-mail) still appear to be at the upper end of the temperature scale. Somewhere I read of someone stating 35°C as his regular operating tenperature after applying the kernel options, which made me wonder.

I have the ML-40 version of the Turion64, running with Edgy Eft (64-bit). Current snapshot after a couple of minutes of operation and swiftfox as well as Rhythmbox running:

TZ1: 16°C
TZ2: 52°C
TZ3: 56°C

Could some of you share your experiences? I set up a poll as well, which would be helpful in getting the big picture instead of having to go through the massive amount of replies that I am sure can be expected for this thread.

TIA and regards

Matthias

---

### Post by RandomJoe on 2007-01-08
Now see, here's the problem with voting in a poll before reading the first post... :rolleyes: Ignore my "below 40C" vote since it's not for a Turion...!  (Probably should have had a clue thanks to the title anyway...)

---

### Post by zgornel on 2007-01-08
50-60 degrees is safe. Over 60 degrees you should start worrying. Over 70 is trouble. This goes for all mobile processors.

---

