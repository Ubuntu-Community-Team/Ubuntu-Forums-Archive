---
title: "No hdmi sound with Asus GeForce 210 after reinstall mythbuntu"
date: 2012-10-27
forum: Hardware
---

### Post by HaghDK on 2012-10-27
I have some serious problem with the sound output of my Asus Geforce 210. I had a crash on my Mythbuntu 12.04 installation and for some unknown reason I cannot get the audio back after a complete reinstall. I have tried almost anything, but to no avail.

my /etc/asound.conf looks like this:

```
pcm.!default {
        type plug
        slave {
                pcm "hw0,7"
                rate 48000
        }
}

```

and I have this in /etc/modprobe.d/sound.conf

```
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

```

and finally I have this in /etc/pulse/default.pa
```
load-module module-alsa-sink device=hw:0,7

```

When I do an aplay -l I get this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
aplay -D plughw:0,7 test.wav
``` gives me
```
Playing WAVE 'test.wav' : Unsigned 8 bit, Rate 22050 Hz, Mono
```

But no sound at all.

Are there something I have completely missed?

---

### Post by HaghDK on 2012-10-27
Problem solved! Had to enable nvidia drivers!

---

