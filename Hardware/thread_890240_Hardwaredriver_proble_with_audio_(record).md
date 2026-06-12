---
title: "Hardware/driver proble with audio (record) ?"
date: 2008-08-14
forum: Hardware
---

### Post by Pierrot Lafouine on 2008-08-14
Hi
I tried to record my voice (with a mic) with the application
located in : Applications/Sound&Video/Sound Recorder
but doesn't work.  I tried to record with all inputs available
tru GUI:
+Front Mic Boost (what is this ?)
+Mic Boost (what is this ?)
+IEC958
+ Capture
+ Capture1
+ Capture2
+ Digital
There is no sound coming out when I hit PLAY when record is over.

I tried another GUI application in:System/Preferences/Sound
All Test buttons worked fine (I was able to hear sounds), except
one button didn't work : Sound capture. When I hit this button, a
DialogBox show this error message:
Failed to construct test pipeline for 'gconfaudiosrc!
audioconvertert ! audioresample ! gconfaudiosink prfile = chat'

What is the next step to make my hardware works fine ?
That my audio driver is ok ?


Thanks

---

### Post by apche93 on 2008-08-16
ok, i had a similar problem until i installed PulseAudio.

Just go to this Ubuntu Wiki:
[URL="https://wiki.ubuntu.com/PulseAudio"]
https://wiki.ubuntu.com/PulseAudio[/URL]

and install PulseAudio.  After that, everything will start working again!


Hope this helps!

---

