---
title: "No sound for HDMI on Samsung R580 (Ubuntu 12.04)"
date: 2012-06-10
forum: Hardware
---

### Post by cjbrooker on 2012-06-10
Hi,

I have a Samsung R580 laptop running Ubuntu 12.04.

Everything works great on it with the latest version of Ubuntu except when I plug in my HDMI cable to connect it to the TV. I can't get the sound through the TV. The sound still comes through the laptop. Picture is fine through the TV.

It has an NVIDIA graphics card and I'm using the proprietry drivers for that.

The output of 'aplay -l' is as follows:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
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
chris@chris-laptop:~$ 
```

Any help on how to fix this appreciated.

---

### Post by gordintoronto on 2012-06-10
From the volume control in your panel, run Sound Settings. Select the Hardware tab. Select one of the HDMI devices. If that doesn't work, keep going though the HDMI devices.

I have the same issue with my laptop, the video works immediately, but to get sound from the TV, I have to change the device.

---

### Post by cjbrooker on 2012-06-11
Thanks. That worked!

I'm sure I tried that before but it worked once I selected HDMI/Display Port 4 from Sound Settings -> Output.

---

