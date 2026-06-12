---
title: "Via VT1708S Front Panel"
date: 2010-12-22
forum: Hardware
---

### Post by smx-smx on 2010-12-22
Hi all.
I have a Via Technologies VT1708S chip (included in my motherboard Asus P7P55 LX).
The front panel of my computer case it's not working. It has got 2 jacks (mic and headphones), but they doesn't work.
I have another microphone plugged in at the back panel, and it works well.
-The headphones are not broken (they work with windows)
-The microphone it's not broken (it works with windows)
-The output works fine, all speakers works well (5.1 speakers)
-I'm using the lastest ALSA driver (Advanced Linux Sound Architecture Driver Version 1.0.23)
-"Front Mic", "Capture", "Mic Boost", and "Line" are unmuted and at maximum volume.
-Pulse input it's setted to the 2nd mic (the first one it's the rear)
-With "arecord | aplay", i get clicks

Thanks in advance, this new motherboard is giving me a lot of problems (IDE controller doesn't work too)](*,)](*,)](*,)](*,)

---

### Post by Fabrício Ceolin on 2011-05-16
Same problem here!

---

### Post by bgiannes on 2011-06-20
well two things to check, 1st the cases speaker audio jacks plug is plug into the motherboards header (AAFP) and 2nd go to the commandline and run alsamixer and make sure the speakers are on and turned up as 'Master Front' is set to 0 by default.

The mic front are muted also...

---

### Post by smx-smx on 2011-07-05
Solved. The latest updates solved the issue. Now my front panel work as it should:KS

---

