---
title: "Unable to get sound to work (via82xx card)"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by akinwale on 2005-06-12
I just installed the Hoary Hedgehog release, and sound is not working (yes, my speaker's working, plugged in properly and tuned up to the highest volume level). Now this is a very major problem, as everything worked fine in Warty Warthog 4.10 :)

Anyway, I followed ubuntu-geek's instructions in the Hoary Sound Broke? thread, and now I get alsactl errors...

Here's what I get when I try to use the restore command with alsactl

akinwale@defworks:~$ sudo alsactl restore 0
Password:
alsactl: set_control:930: warning: name mismatch (Master Playback Volume/Center Playback Switch) for control #2
alsactl: set_control:1046: bad control.2.value.0 content

Also, when I run alsamixer, I can't adjust the Master and PCM volumes. They're at zero, but I can't increase it, and they're not "off"/muted.

Any ideas how I can get this to work?

Thanks.

---

### Post by Martin Witte on 2005-06-12
alsamixer works with the arrow keys: left/right to go to a channel, up/down to increase/decrease, and 'M' to mute a channel

---

### Post by akinwale on 2005-06-13
Unfortunately it is impossible to adjust the volume levels for the Master and PCM. I can adjust the volume levels of the others just fine using the arrow keys, but Master and PCM remain at zero when I use the up arrow key.

---

