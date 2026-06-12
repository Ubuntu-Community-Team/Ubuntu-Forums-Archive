---
title: "No sound output"
date: 2011-08-18
forum: Hardware
---

### Post by bngsudheer on 2011-08-18
Hello,

From couple of days, there's no sound output on my laptop.

I'm using Unbuntu 11.04. 

Here's some information that might be useful:

When I execute
aplay /usr/share/sounds/alsa/Front_Center.wavI don't hear voice. But on the terminal I see:
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My ALSA information is located at [http://www.alsa-project.org/db/?f=3a8f419e93dbc10e9a2e2245e47e7f9380fcb1ef](http://www.alsa-project.org/db/?f=3a8f419e93dbc10e9a2e2245e47e7f9380fcb1ef)

When I click Sound Preferences from the sound icon on the GNOME panel, the window doesn't launch.


I'd appreciate your help to fix this problem.

---

### Post by bngsudheer on 2011-08-18
I just discovered that sound works on the headsets but not the laptop speakers.

---

### Post by bngsudheer on 2011-08-18
I don't know what happened. Sound is working well now. Sound preferences window is also launching. Thanks for reading this!

---

