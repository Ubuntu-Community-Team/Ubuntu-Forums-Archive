---
title: "No HDMI Sound"
date: 2018-01-26
forum: Hardware
---

### Post by lotsofcoffee on 2018-01-26
Hello everyone,
      I have been searching the forums for help with this, but nothing seems to be working. I have an an older ASUS F50SV-X1 running Ubuntu 16.04.3 LTS.

Trying to do: I am trying to play audio and video over to my TV through HDMI.

Issue: Internal speakers on my laptop work and the video plays to my TV. But when i hook up the HDMI and switch to HDMI in Sound Settings I get nothing. I am sure it is not the cable or TV (i have tried another Win10 laptop and it worked)

Here is the result from aplay -l

sao@sao-F50SV:~$ sudo aplay -l
[sudo] password for sao: 
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 3: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thank you for any help that you can offer

---

