---
title: "HP Pavilion laptop's headphone plug stopped working"
date: 2012-06-08
forum: Hardware
---

### Post by Shrikee7973 on 2012-06-08
I've installed 12.04 LTS a while ago, no problems at all until this day. The laptop's (two) headphone plugs stopped working. It was working before, and I even checked it with the live CD (also 12.04), the live CD could play .flac files through my headphones with no problem at all. I've tried to play with sound settings, alsa mixer (GUI version also), and couldn't solve the problem. 

Background information: today I've installed an audio player called 'Deadbeef' to play bit perfect audio on my USB External sound card... installed it from an imported repository, set some options in preferences (use the output device, use alsa plugin, use alsa resample: OFF, and release device after playing: ON). It works okay, my external sound card sounds great this way. Reverting the options to default didn't solve the problem.

---

### Post by Shrikee7973 on 2012-06-08
I just hope the solution isn't like this: re-install operating system and don't use deadbeef...

---

### Post by Shrikee7973 on 2012-06-09
[SOLVED] : I've used a line 'options snd-hda-intel single_cmd=1' in /etc/modprobe.d/alsa-base.conf  as a workaround for shutdown noise... Removing it made the headphone jack work ....  but the laptop is making the noise again on restart... :(

---

