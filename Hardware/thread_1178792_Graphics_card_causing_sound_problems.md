---
title: "Graphics card causing sound problems?"
date: 2009-06-04
forum: Hardware
---

### Post by kaiz0r.ku on 2009-06-04
Ubuntu thinks that my Videocard is my playback device for sound, so it overrides ALSA. I have onboard sound: realtek ALC889A. 

This is what it says in Terminal when i type aplay -l:
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have installed ALSA drivers from the Realtek website, but I don't know how to override this? is there a way i can uninstall these drivers? or just blacklist them? any help woul dbe useful!

I have an Asus EAH4850 Graphics card... running on ATI's Propriety Drivers.

---

### Post by kaiz0r.ku on 2009-06-04
Actually its solved. Dont worry

---

