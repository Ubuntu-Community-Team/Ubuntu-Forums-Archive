---
title: "My sound has died - can't restart it!"
date: 2010-01-30
forum: Hardware
---

### Post by AussieGuy on 2010-01-30
For no reason that I can think of, the sound on my Lenovo T500 Thinkpad running 9.10 has just stopped working.  I've checked alsamixer, done a 

sudo /etc/init.d/alsa-utils restart

checked for processes which might have been using sound using

lsof | grep pcm

(only pulseaudio was listed), but nothing so far has worked.  The machine remains mute.  I guess I could always reboot, but surely there's something else less drastic?

Thanks,
-A.

---

### Post by IcarusR on 2010-01-30
Why do you call a reboot drastic ? It's laptop not a server.
Rebooting may resolve your issue, which may not re-occur.

---

