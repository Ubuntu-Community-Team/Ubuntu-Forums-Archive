---
title: "Webcam stopped working with Skype, works with everything else"
date: 2014-10-11
forum: Hardware
---

### Post by Graeme_Pietersz on 2014-10-11
My webcam has (as of yesterday) stopped working with Skype on Kubuntu 14.04 . It says "no devices found"

It works with everything else. A video device does not show in the Phonon audio and video settings though.

trying to start Skype with  LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so

gives me:

ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded (failed to map segment from shared object): ignored.

I tried reinstalling libv4l, no change.

I need Skype for work on Monday, so would be very grateful for help.

---

