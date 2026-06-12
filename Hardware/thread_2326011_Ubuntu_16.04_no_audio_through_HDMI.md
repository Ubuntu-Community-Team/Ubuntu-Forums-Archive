---
title: "Ubuntu 16.04 no audio through HDMI"
date: 2016-05-27
forum: Hardware
---

### Post by jack-r-davis-jr on 2016-05-27
I have Ubuntu 16.04 LTS installed on my laptop.  The sound works fine through the laptop speakers, but when I plug an HDMI cable in and connect it to my Onkyo surround system, I get no sound.

I can bring up the sound app and select HDMI but when I click test I get nothing.

I've tried installing alsamixer and making sure that the volume is up and nothing is muted.

I know it's not the HDMI port because it works fine when I boot the laptop to Windows.

Anyone else run into this problem?

---

### Post by QDR06VV9 on 2016-05-27
Maybe you already know this already but worth a second mention you also have to tell the Video application IE: VLC, Smplayer, Kodi to specifically use HDMI port.
And if there is still no sound post back the return of this from the terminal
```
sudo aplay -l 

```
Regards

---

### Post by jack-r-davis-jr on 2016-05-27
Still no sound.  I tried removing the pulse config files in .config/pulse and restarting pulseaudio.
 
Here's the output from aplay -l

```

**** List of PLAYBACK Hardware Devices ****
Home directory not accessible: Permission denied
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3236 Analog [ALC3236 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by jack-r-davis-jr on 2016-05-27
I looked into the Home directory not accessible error.  I did
```

chown -R sonny:sonny /home/sonny

```

because there was one directory in my home directory that was owned by root.  When I ran aplay -l again, I got the same result.

---

