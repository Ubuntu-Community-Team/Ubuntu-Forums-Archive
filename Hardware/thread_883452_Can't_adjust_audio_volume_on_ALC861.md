---
title: "Can't adjust audio volume on ALC861"
date: 2008-08-08
forum: Hardware
---

### Post by vivow on 2008-08-08
Hey

I recently installed Ubuntu. Everything seems to work fine except for the audio device. I have a buildin Realtek HDA ACL861 audiocard. I can hear sound, thats not the problem,
but the volume level (master and pcm2) is set to MAX and when I try lowering it, it jumps right back to the top.
I reinstalled alsa via packet manager, compiled a new kernel with the latest 1.0.17 drivers from the homepage, played a bit with the audio device settings.
Alsa does recognize my card as alc861, so I have no idea what else I could do to fix that problem. I'm about to become deaf.

thanks in advance.

ps, also commmand line "alsamixer" doesnt work:
alsamixer: function snd_mixer_load failed: No such file or directory

---

### Post by vivow on 2008-08-08
Does no one have any idea?
I really would appreciate any kind of help.

---

### Post by qgfreire on 2008-08-27
It's solved?
If not, see [http://ubuntuforums.org/showthread.php?t=901934](http://ubuntuforums.org/showthread.php?t=901934)
FGF

---

