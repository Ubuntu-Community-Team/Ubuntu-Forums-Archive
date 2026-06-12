---
title: "Can't get my audio working"
date: 2016-08-28
forum: Hardware
---

### Post by ja-castropizzo on 2016-08-28
```
 cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7d10000 irq 30

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT1802 Analog [VT1802 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: VT1802 Alt Analog [VT1802 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

my computer does see the card, but when I want to configure the output, all i get is the dummy one

Thank you all

---

### Post by Bucky Ball on 2016-08-29
Welcome. Are you using straight Ubuntu or one of the flavours? Which release number? What exactly are you trying to do (output from what to where and which device: internal or external)? Best to look in Pulseaudio Volume Control and tweak the settings there before getting elbow deep in code. It may be that simple.

---

### Post by ja-castropizzo on 2016-08-29
Puseaudio Volume Control has just the Dummy Output.
```
 cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
NAME="Ubuntu"
VERSION="16.04.1 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.1 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
UBUNTU_CODENAME=xenial

```

I've had the same problem with the 14.04. I thought that I could solve it by updating it, but it may seem that I couldn't.

---

