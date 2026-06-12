---
title: "Webcam + Microphone problems.."
date: 2011-04-06
forum: Hardware
---

### Post by HDVries on 2011-04-06
Hey,

Well like i got a webcam and mic in my laptop but my webcam doesnt work very often, sometimes it does and sometimes it doesnt and i dont remember my microphone working at all.. I have no clue what to do since im new to ubuntu

Thanks for helping :KS

---

### Post by mikewhatever on 2011-04-06
You could tryproviding some useful info:
- laptop model
- version of Ubuntu
- 32/64 bit
- outputs of 'lsusb' and 'aplay -l'
- how you test the webcam

---

### Post by HDVries on 2011-04-08
> **mikewhatever said:**
> You could tryproviding some useful info:
- laptop model
- version of Ubuntu
- 32/64 bit
- outputs of 'lsusb' and 'aplay -l'
- how you test the webcam

```
laptop@ubuntu:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:1293 Apple, Inc. 
Bus 001 Device 002: ID 04f2:b153 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
laptop@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm pretty sure its 32 bits
Ubuntu 10.04.2 LTS
and my laptop is a HP Compaq Presario CQ61-445ed

I test my cam through Camorama

---

### Post by mikewhatever on 2011-04-09
Right, thanks for the output. The webcam seems to be this:
```
Bus 001 Device 002: ID 04f2:b153 Chicony Electronics Co., Ltd 
```

... and according to [http://hardware4linux.info]("http://hardware4linux.info/component/27034/"), it is supported. Have you tried anything other then Camorama?

As for the mic, do make sure it's not muted in the Input tab of Sound Preferences.

---

### Post by webmasterraj1 on 2011-04-09
> **mikewhatever said:**
> Right, thanks for the output. The webcam seems to be this:
```
Bus 001 Device 002: ID 04f2:b153 Chicony Electronics Co., Ltd 
```... and according to [http://hardware4linux.info]("http://hardware4linux.info/component/27034/"), it is supported. Have you tried anything other then Camorama?

As for the mic, do make sure it's not muted in the Input tab of Sound Preferences.

  According to me this post is really very good.
Thanks for this nice post.

---

### Post by HDVries on 2011-04-10
> **mikewhatever said:**
> Right, thanks for the output. The webcam seems to be this:
```
Bus 001 Device 002: ID 04f2:b153 Chicony Electronics Co., Ltd 
```

... and according to [http://hardware4linux.info]("http://hardware4linux.info/component/27034/"), it is supported. Have you tried anything other then Camorama?

As for the mic, do make sure it's not muted in the Input tab of Sound Preferences.

Well the webcam only works sometimes.. It usually works after midnight if i reboot.. But i tried with guvcview, adobe flash player, msn and skype as for the mic, it is a teamspeak problem

---

