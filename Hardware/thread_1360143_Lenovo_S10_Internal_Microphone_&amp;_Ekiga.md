---
title: "Lenovo S10 Internal Microphone &amp; Ekiga"
date: 2009-12-20
forum: Hardware
---

### Post by Rifester on 2009-12-20
I have set my parents up with Ekiga on their Windows machine and we have successfully linked up via video (so they can see their grandchildren).  I can hear my parents fine via their internal microphone but I am having problems with mine.   I have read many google and forum posts about this bug.   The microphone is detecting sound after I switched to Microphone Two in the sound mixer "Sound Preferences".   However, for my parents to hear me at all I have to amplify the microphone and they can barely here me or I get a bunch of feedback?   Any suggestions?  I am using 9.10 and have checked to see that I have the most updated version of ALSA.

Thanks for helping me learn!

Mark

---

### Post by mikewhatever on 2009-12-20
Perhaps you should use micboost. Check if you have that option by typing <alsamixer> in Terminal and cycling through channels with Tab key.

---

### Post by Rifester on 2009-12-21
Mikewhatever,
Thank you, this fixed the problem.   Micboost was all the way down to 0, after adjusting it up to just below the red level it is working perfectly.   I know there are a lot of people out there with this problem.   Thank you so much!  No my kids will be able to video chat with their grand parents over the holidays!

Mark

---

