---
title: "[SOLVED] No sound after nvidia driver upgrade"
date: 2008-05-30
forum: Hardware
---

### Post by bigtoedsloth on 2008-05-30
I just tried installing the latest nvidia binary driver (173.14.05) - by downloading from the nvidia site and installing manually.  I've previously installed the nvidia binary drivers that way without issues.

This time I lost all sound after the install!  I am using Intel onboard audio.

How are the two (video and audio) related?  How might I resolve this issue (apart from a regression to the previous version of the driver)?

---

### Post by bigtoedsloth on 2008-07-06
It turns out that the new version of the nvidia driver enables digital audio over HDMI.  So (I don't understand why) the digital audio must now be used in preference to the analogue audio (or some such).  It's good news for me, since audio over HDMI is actually exactly what I want, but it was certainly confusing ...

---

