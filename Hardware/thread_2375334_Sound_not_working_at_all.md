---
title: "Sound not working at all"
date: 2017-10-23
forum: Hardware
---

### Post by lpupo on 2017-10-23
I'm a brand new Linux user.Today my sound stopped working completely after i installed deluge and vlc.
At first i went to sound settings and it looked pretty normal.When i restarted the computer all the devices on the output and input tabs disappeared.It doesn't recognize when i plug in headphones either.
Here is an alsa information script i just ran:    [http://www.alsa-project.org/db/?f=a0cb02d88bf43ab01731041778c9c428aeaa01ff](http://www.alsa-project.org/db/?f=a0cb02d88bf43ab01731041778c9c428aeaa01ff)
What else can i do?
Thx!

---

### Post by TheFu on 2017-10-24
If you aren't running Lubuntu, then pulse audio is likely in control.  It has a habit of locking up/dying.  Kill pulse audio and restart it - I have to do this whenever I change the program that is trying to output audio.  Another thread this morning asked a similar question and provided the answer (I replied to it too).  Search the forums for that thread.

Never had this issue prior to pulse being forced onto us.  ALSA sucked until I manually configured it, but after that, it just worked, always, for years.  Pulse has never worked reliably for me. NEVER.

---

### Post by Yellow Pasque on 2017-10-24
Rant all you want, but this isn't a pulseaudio problem:
```
[   15.484065] snd_hda_intel 0000:00:1f.3: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   16.492166] snd_hda_intel 0000:00:1f.3: No response from codec, disabling MSI: last cmd=0x000f0000
[   17.500276] snd_hda_intel 0000:00:1f.3: Codec #0 probe error; disabling it...
```

I would try disabling the audio codec in the BIOS, booting, and then reenabling the codec in the BIOS. Or I would try resetting BIOS to default settings.

---

