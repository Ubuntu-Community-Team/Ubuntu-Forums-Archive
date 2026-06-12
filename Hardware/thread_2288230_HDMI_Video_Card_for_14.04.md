---
title: "HDMI Video Card for 14.04"
date: 2015-07-25
forum: Hardware
---

### Post by robn30 on 2015-07-25
I am looking for a card that will pass audio over HDMI.  I would like it to work in passthrough mode but PCM will be fine if that's all that is possible.  I am looking to spend less than $50.  I know Nvidia is normally the way to go on Linux machines but I figure by this point maybe ATI has had some advancements, but I'm not sure.  I was hoping the community here could provide me some ideas on which option would be best.  No gaming will be done on this machine so video and audio over HDMI are the only requirements.  I was looking at the Radeon HD5450 or the GeForce GT 210 as options.  Those are just the basic cards that I know do audio over HDMI.  I am open to other options, especially if they are better.  Thanks as always to the knowledge base within this community.

---

### Post by TheFu on 2015-07-25
The build-in Intel GPUs work.  Using an Intel G3258 right now with Kodi - 5.1 DTS audio.

And I've used built-in Radeon 53xx with both proprietary and OSS drivers. Worked. That box is a router now.

The machines I have with nVidia GPUs .. well, I haven't tried any sounds in years. They don't have a GUI, so testing audio isn't really possible.  It has a GF108 [GeForce GT 430] according to **lshw**.

**aplay** says it should work

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

