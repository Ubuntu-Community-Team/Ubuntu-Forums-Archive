---
title: "Sound doesn't work"
date: 2008-05-09
forum: Hardware
---

### Post by Jordanwb on 2008-05-09
I installed Ubuntu 8.04 last night onto my computer using the Alternate Installer. In the Live CD and in 7.10 my sound card works but it doesn't now in 8.04. It's a Creative Audigy Sound Blaster 0090 series. I have all the updates. The speakers are plugged in and turned on. In volume control all output related controls are unmuted and at 75%.

---

### Post by Jordanwb on 2008-05-09
I figured out (well not really) what the problem was. My sound card supports Digital Output (it's a surround sound card). See [http://ubuntuforums.org/showthread.php?t=769850&highlight=sound&page=10](http://ubuntuforums.org/showthread.php?t=769850&highlight=sound&page=10) post #97,

> 
I just fixed (I think) my own problem, and I am posting it for everyone else.

I had loud static sound coming from my speakers, and it finally went away when I went to System>Prefs>Volume Control>Switches(tab) and unchecked my output jack. Ever since then everything has worked fine, and I can play multiple sound files off different platforms at the same time.

Also, my sound prefs are all under PulseAudio, I don't know how much that impacts it.

Hope this helps someone.


That was it. Digital Output.

---

