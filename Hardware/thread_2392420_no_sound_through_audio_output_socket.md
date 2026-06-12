---
title: "no sound through audio output socket"
date: 2018-05-21
forum: Hardware
---

### Post by engine on 2018-05-21
Yesterday I was listening to YouTube play-back through a USB headset. I also checked a midi file (something I'd made) with timidity, using the same USB headset. This morning, timidity is still playing through the USB headset: but YouTube isn't. YouTube isn't playing through the normal analogue/audio output either.
[LIST][*]on the Playback tab, the Pulse Audio volume control dialogue shows only ALSA plug-in[timidity]
[*]on the Output devices tab, 'built-in analog stereo' is selected, headphones are shown as 'plugged in' and the output level is 47%.[/LIST]

What do I have to do to get everything playing through the audio output? I don't want to use the USB headset any more. Thanks in advance.

---

### Post by pete-br on 2018-05-25
Use the Ubuntu help:
[https://help.ubuntu.com/lts/ubuntu-help/sound-usespeakers.html](https://help.ubuntu.com/lts/ubuntu-help/sound-usespeakers.html)

---

### Post by leunam12 on 2018-05-25
In the Output Devices tab there should be a field that says "Connector", you have to change that to "Line Out" or "speakers".

---

### Post by kerry_s on 2018-05-25
try running this, it's what i use in my script to change mine back after using hdmi.
```
pactl --server "unix:/run/user/$(id -u)/pulse/native" set-card-profile 0 output:analog-stereo
```

---

