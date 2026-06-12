---
title: "No HDMI sound Dell Xps"
date: 2013-04-26
forum: Hardware
---

### Post by marcoisaac on 2013-04-26
Hi i have a Dell Xps 1640 and my problem is that when i connect my laptop to a TV  the video is ok but the sound is still in the laptop speakers. this is my information.
thanks

tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


i already tried to change in the pulse audio settings but the hdmi output doesnt appear in the options thanks

---

### Post by blackdalek on 2013-04-26
I have same problem with Dell Inspiron 3520. HDMI sound output worked in 12.10 but HDMI sound output device no longer exists in 13.04.

I think this is the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984)

---

### Post by ppjdee on 2013-04-27
I found the 3.9rc8 kernel fixed my hdmi problems. Im using the ati beta drivers from amd site.

[http://ubuntuforums.org/showthread.php?t=2136493&page=4](http://ubuntuforums.org/showthread.php?t=2136493&page=4)

---

