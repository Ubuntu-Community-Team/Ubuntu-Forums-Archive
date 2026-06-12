---
title: "No sound in Lenovo Y530"
date: 2009-10-27
forum: Hardware
---

### Post by mady4u on 2009-10-27
I have installed Ubuntu 9.04 on my Lenovo Y530 in a separate partition along with Vista.

Now the problem is that there is no sound if I am using Ubuntu, Vista is fine. I checked many websites but no solution helped.


root@lenovo:/media/Music/Hindi# aplay Zara\ Sa.mp3 
Playing raw data 'Zara Sa.mp3' : Unsigned 8 bit, Rate 8000 Hz, Mono
^CAborted by signal Interrupt...



root@lenovo:/# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

