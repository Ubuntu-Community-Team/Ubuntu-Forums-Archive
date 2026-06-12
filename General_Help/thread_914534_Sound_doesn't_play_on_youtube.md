---
title: "Sound doesn't play on youtube"
date: 2008-09-08
forum: General Help
---

### Post by Gdschaf on 2008-09-08
i don't know why, but the first few times i used ubuntu, the sound from youtube worked, and now nothing, the video plays but nothing else does, does ne one have ne idea of why that would happen?

---

### Post by mb_webguy on 2008-09-08
Do you have another application open such as a media player or anything else that might produce sound?  If so, it sounds like a common Flash/PulseAudio incompatibility problem.  Installing the Flash 10 plugin from the backports repository should solve the problem.  You might want to check the links in my signature, both for the Flash 10 plugin and the PulseAudio fixes.

---

### Post by mempman on 2008-09-08
> **Gdschaf said:**
> i don't know why, but the first few times i used ubuntu, the sound from youtube worked, and now nothing, the video plays but nothing else does, does ne one have ne idea of why that would happen?

Try This:

1- close all your browsers
2- issue the following command: "sudo pulseaudio -k"
3- start ur browsers and try out youtube.com

* make sure that during the above process you don't have any audio playing programs open.

---

### Post by Gdschaf on 2008-09-08
following the pulse audio and flash 10 plugin worked perfectly, im sry to report the other sulotion listed by the other user didn't work but im just glad i can listen to music on youtube now :-)

---

### Post by Robbinski12 on 2008-10-02
It says 'Failed to kill daemon' to me!

---

### Post by Gdschaf on 2009-06-04
yeah it says that to me now with ubuntu 9.04

---

### Post by Mirge on 2009-06-04
Make sure "PCM" is turned up in your volume control.

---

