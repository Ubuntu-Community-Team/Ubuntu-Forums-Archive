---
title: "Creative SB X-Fi &amp; OSS Woes"
date: 2008-07-17
forum: Hardware
---

### Post by freeloader105 on 2008-07-17
I'm having some issues with OSS and my Creative SB X-Fi XtremeGamer Fatal1ty Pro Series Card. The Ubuntu system sounds and music playback are fine, but I get no sound in WINE (and going into WINE's settings and setting OSS as the audio driver made Counter-Strike crash). Also, in Sound preferences, the audio driver is set to 'autodetect' by default. When I try to set it to OSS and run the test sound, it gives the following error message:

'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.'

Even if I didn't have any music or movies playing in the background at the time of running the test sound.

Anyone know how I can resolve this?


Side info: I tried installing Creative's official Beta driver for ALSA but wasn't able to complete the installation. Also, I found out that I probably need to recompile the kernel in order to get it to work (very user-friendly, Creative, nice going!) so I scratched that idea and installed OSS according to this guide:
[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2) . I removed the ALSA packages in the way the guide suggested. Currently, the only ALSA package that remains is 'alsa-utils'.

Miscellaneous question: does either the ALSA or the OSS driver support EAX? Also, is there any sound card company that releases native linux drivers?

---

### Post by Yellow Pasque on 2008-07-28
Sorry I just saw this now. Are you running system sounds (ESD?) If so, I would try disabling that and seeing if the WINE error persists. If it does, what does this show?:
```
cat /dev/sndstat
```

---

