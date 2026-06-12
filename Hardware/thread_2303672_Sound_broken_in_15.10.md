---
title: "Sound broken in 15.10"
date: 2015-11-20
forum: Hardware
---

### Post by pickarooney on 2015-11-20
I have no sound in most programs (guayadeque music, mplayer, YouTube...) though it does work in some websites.

If I try to play a video file in mplayer I get this

AO: [pulse] pa_stream_get_latency() failed: Connection terminated

if I play the same file in VLC I get this

[081e23f0] pulse audio output error: cannot write: Bad state

This happened after updating from 15.04 to 15.10 last night.

Occasionally sound will work in VLC but then it's as if pulseaudio crashes and I can't play anything any more.

---

### Post by pickarooney on 2015-11-20
After trying all sorts of stuff from all corners of the internet, I found this comment buried in a thread, with no thanks or thumbs up and, as far as I can tell, this has restored sound

> locate the .pulse folder in your home folder. Most probably its going to be under .config. Remove the .pulse folder. Logout and login. That should do the trick. 

[http://askubuntu.com/questions/613370/no-audio-after-updating-to-15-04](http://askubuntu.com/questions/613370/no-audio-after-updating-to-15-04)

---

