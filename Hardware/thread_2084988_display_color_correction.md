---
title: "display color correction"
date: 2012-11-17
forum: Hardware
---

### Post by sciguy125 on 2012-11-17
I've been playing with the color correction on my system but I can't seem to get it working properly.  Of course, it could just be that I don't fully understand how it works...

system settings > color, I select my monitor, click add profile and it lets me select a profile.  I presume that it automatically downloaded the ICC profile (either from the internet or the manufacturer stores it on the display somehow).  At this point, it has the profile, but it doesn't seem to be doing any sort of correction because the screen looks the same.  Does it only work with specific programs, or should it work for the entire system?

I realize that getting the appropriate hardware to calibrate it myself would be better, but this is what I have...  I also know that the profile it found isn't garbage.  The TRC tab for the profile shows that the display doesn't have enough red (red curve is low).  Sure enough, the display looks too blue/green (and always has).

Am I doing something wrong, or are my expectations incorrect?  I was expecting it to change the entire screen (as if playing with the gamma settings in X).

Edit: I should also point out that I'm on a laptop that has an external display connected (so 2 displays total).  I have the external display set to the factory defaults.  Obviously, the internal display only gives me control over brightness.  The internal display is the one with the blue tinge I mentioned.

---

### Post by sciguy125 on 2012-12-13
To answer my own question, it looks like the "default" profiles were grabbed from EDID.  I don't know exactly what they are, but they are not sufficient for display correction.  I got a colorimeter to profile the displays and those profiles loaded and were used as expected.

---

