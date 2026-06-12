---
title: "HDMI Audio With Dell M1330 GeForce 8400M Intel HDA"
date: 2009-04-30
forum: Hardware
---

### Post by JamieKitson on 2009-04-30
Just thought this might save someone else the time that I wasted.

My stumbling block was that I was expecting to see a separate HDMI audio device. aplay -l actually shows the HDMI output as a digital subdevice of my soundcard. ie:
```

jamie@jamie-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Once it has dawned on me that this was ok I played around in alsamixer until I got sound from the TV, unmuting IEC958 and setting IEC958 Playback Source to Digital.

---

### Post by Gausian on 2009-05-02
This is also how i got audio from the hdmi port.

One thing that doesnt work for me though is using the media remote to change volume levels while watching movies.

Strangely, it works when just sitting in from of the computer.  But when i hook up the tv, the remote adjusts the master volume, but has no effect on actual volume.

---

