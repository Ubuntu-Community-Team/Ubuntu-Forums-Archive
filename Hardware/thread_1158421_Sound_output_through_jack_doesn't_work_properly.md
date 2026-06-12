---
title: "Sound output through jack doesn't work properly"
date: 2009-05-13
forum: Hardware
---

### Post by dougiehouser on 2009-05-13
Hi,
I recently installed Ubuntu 9.04 onto one of my desktops and encountered problems with sound (sound worked fine in windows before this). The computer motherboard has onboard Realtek sound and my speakers are plugged into the rear speaker output socket.

Sound problems are well documented on this website and others, so I have tried various solutions (installing Realtek drivers + re-doing ALSA + some others) without any success.

In frustration I tried plugging the speakers into the various other speaker outputs on the back on the mboard and found something really weird. With the speaker jack plugged halfway into the rear speaker socket (the one I was originally using) there was sound but quiet with some background noise. With the jack fully plugged in there was again no sound.

After some searching it seems that people have had similar problems except the other way round but on laptops rather than desktops. Something to do with the mute when something is plugged into a sound socket maybe, but I haven't been able to work out how this could apply to me.

Does anyone have any ideas on how to fix this?

---

### Post by dougiehouser on 2009-05-14
After re-installing the realtek driver and then modifying the asla-base and sound files, the audio output has moved to the black socket but at least it works.

---

