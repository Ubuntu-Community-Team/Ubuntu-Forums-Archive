---
title: "USB headset stopped working."
date: 2009-08-01
forum: Hardware
---

### Post by mooreted on 2009-08-01
I have been using my USB headset for Skype for about a month with now problems. I did recently install ZoneMinder. Don't know if that makes a difference, but now my headset doesn't work at all. When I try to test it in System/Preferences/Sound I get:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

aplay -l shows:

**** List of PLAYBACK Hardware Devices ****
card 1: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: U0xd8c0x0c [USB Device 0xd8c:0x0c], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have been to about 20 or 30 posts here and all over the Internet. Can't find a solution.

---

