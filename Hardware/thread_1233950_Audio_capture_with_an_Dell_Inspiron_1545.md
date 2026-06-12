---
title: "Audio capture with an Dell Inspiron 1545"
date: 2009-08-07
forum: Hardware
---

### Post by donmatas on 2009-08-07
Hello ubunteros:

i have a Dell 1545 with an Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03).

I can't record sound with the microphone (so i can't use skype). I tried to fix it editing the alsa-base.conf adding this script but it doesn't works:
options snd-hda-intel model=hp
options snd-hda-intel enable_msi=1
#options snd-hda-intel model=3stack-dig
#options snd-hda-intel enable_msi=1
#options snd-hda-intel single_cmd=1

I have Janunty Jackalope (the audio device works perfectly with hardy heron)

thanks
M

---

