---
title: "Logitech x920 microphone not working"
date: 2020-04-05
forum: Hardware
---

### Post by fishwebby on 2020-04-05
My Logitech c920 microphone doesn't seem to be working, but it was previously. The video does work, and the microphone shows up in the audio settings, and in alsamixer. Nowhere is it muted. The output of ```
arecord -l
``` is this:

```
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: ALC887-VD Alt Analog [ALC887-VD Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: C920 [HD Pro Webcam C920], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I'm using Xubuntu 18.04. Any help is greatly appreciated!

---

### Post by TheFu on 2020-04-05
try this
[https://ubuntuforums.org/showthread.php?t=2440021&p=13944201#post13944201](https://ubuntuforums.org/showthread.php?t=2440021&p=13944201#post13944201)

---

### Post by fishwebby on 2020-04-06
Thanks! Actually with tinkering and a reboot it's just started working, but unfortunately I don't know what I did! I'll keep an eye on it...

---

