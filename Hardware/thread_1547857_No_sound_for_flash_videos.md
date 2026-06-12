---
title: "No sound for flash videos"
date: 2010-08-07
forum: Hardware
---

### Post by zzzliperzzz on 2010-08-07
Hello folks,

I tried to play music using the pre-installed music player and
the sound is working but when I try to watch a video in youtube 
it does not play any sound. I also tried watching in facebook and the same thing
happens. I hope someone will help me with this problem. Thanks.

---

### Post by ajgreeny on 2010-08-07
Run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

