---
title: "Audio background noise on Asus K50IJ"
date: 2014-04-23
forum: Hardware
---

### Post by gattolor on 2014-04-23
Hi,
I'm currently using Xubuntu 14.04 live (the same thing happens with the standard Ubuntu) and a background noise starts as soon as I start playing audio (and continues forever).
I've looked at old threads like this [http://ubuntuforums.org/showthread.php?t=1204735&highlight=asus+K50IJ](http://ubuntuforums.org/showthread.php?t=1204735&highlight=asus+K50IJ) that say to put PCM at 100%, but it is already at 100%.
Any advices?

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: VT1708S Alt Analog [VT1708S Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by gattolor on 2014-04-23
I correct myself
the problem seems to appear only from youtube,
and if I pause the video and play a local file after a while it disappears.
If I open the local file just after having paused the video it doesn't work, I have to wait something like 10 seconds.
And the noise starts again after making the yt video play again.
This thing is so strange

---

