---
title: "Sounds Inexplicably Stops Working"
date: 2008-05-15
forum: Hardware
---

### Post by sunmorgus on 2008-05-15
Installed Ubuntu 8.04 recently, using linux for my first time, and have been loving it so far. Everything works properly except for one tiny annoyance...my sound will just inexplicably stop working from time to time. It mostly affects pidgin, which is odd, and flash based video on the web and only when I mute or adjust the volume from the buttons on my keyboard. If I do that, then audio in pidgin will stop working. Sometimes just going up the the audio panel icon and muting and un-muting will fix it, sometimes I have to restart, sometimes restarting pidgin will fix it, I have tried sudo alsa force-reload and that will fix the audio as well, but I would like for it to just always work. I am using a Realtek HD Audio codec device on my HP dc5750, the problem occured both with the driver that was installed when I set up ubuntu and I downloaded the driver from realtek and the same issue occurs. Is there anything else that I can try that can prevent this from happening?

---

### Post by gsiliceo on 2008-05-15
In system > preferences > audio, select ALSA instead of PULSE or Autodectect. Restart

---

### Post by sunmorgus on 2008-05-16
HDA ATI SB (Alsa mixer) is already selected.

---

