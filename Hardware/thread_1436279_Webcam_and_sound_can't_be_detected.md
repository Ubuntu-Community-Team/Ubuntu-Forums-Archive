---
title: "Webcam and sound can't be detected"
date: 2010-03-22
forum: Hardware
---

### Post by Ruddy88 on 2010-03-22
I have RealTek sound driver i guess when it comes to Windows but i dont know how to install it here on Linux. Im on alienware m15x and i install linux just for fun and i like it. But why there's no sound here, where to find my driver manually? Nothing is muted as i see and in preferences > Sound, i saw "Internal Audio" in my hardware list.

Also my webcam can't be detected here. Any solution?

---

### Post by Newfoundlander on 2010-03-22
What is the brand/model of your webcam?  Does it have its own mic or are you using another mic?  What application are you using to test your webcam?

---

### Post by Yellow Pasque on 2010-03-22
Please post output of:
```
aplay -l
```

---

### Post by Ruddy88 on 2010-03-24
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


That is the output of aplay -l.

As for the webcam, I dont know. It's integrated (built-in), I have alienware m15x

---

### Post by Ruddy88 on 2010-03-28
Webcam works now but I still cant get sound to work, please help someone!

---

