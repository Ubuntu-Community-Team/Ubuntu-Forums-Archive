---
title: "Hard Shutdown makes Audio stop working. (dummy output)"
date: 2010-05-06
forum: Hardware
---

### Post by Sepero on 2010-05-06
I'm on Lucid and had this same problem on Karmic. If the machine is hard shutdown (powered off by holding the power button, or electrical outage), then on next boot, the audio device will not be recognized.

I resolved this by following the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)


Steps
[LIST=1]
[*]Edit this file:
sudo gedit /etc/modprobe.d/alsa-base-conf


[*]Append this line to the end of the file:
options snd-hda-intel probe_mask=1 model=auto
[/LIST]


thank you

keywords:
sound preferences

---

