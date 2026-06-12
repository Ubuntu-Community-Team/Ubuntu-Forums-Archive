---
title: "Speakers dont work only on Ubuntu on a dual boot system"
date: 2010-09-03
forum: Hardware
---

### Post by anjumara on 2010-09-03
Hi,
       I have Dell Studio15, the speakers on my laptop don't work. I tried a few things seeing other solved issues but they dint help in this case. There is no problem with the hardware as it works perfectly fine on by other OS that  is windows7. I want to completely shift over to Ubuntu please help me to fix this up.
-----------------------------------------------------------------------------------------------------------------------------------
uname -a
Linux anjum-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
-----------------------------------------------------------------------------------------------------------------------------------

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
-----------------------------------------------------------------------------------------------------------------------------------
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
--------------------------------------------------------------------------------------------------------------------------------
head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD73C1X5

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
------------------------------------------------------------------------------------------------------------------------------

---

