---
title: "2011 iMac external insignia speakers very quiet 14.04"
date: 2015-09-28
forum: Hardware
---

### Post by joshklann on 2015-09-28
My computer recognizes when I plug/unplug my speakers. Unplugged the internal speakers play with normal volume. I opened alsamixer in a terminal and turned all the volume levels to 100.
This mac has the: intel core i5-2400s cpu @ 2.5GHz x 4, AMD Radeon 6600M and 6700M series, 14.04 LTS trusty tar.

I plugged this into the terminal as other forums have asked for this information while dealing with sound issues.

joshua@ubuntu:~$ uname -a
Linux ubuntu 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
joshua@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: Cirrus Digital [Cirrus Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
joshua@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
joshua@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Cirrus Logic CS4206

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

---

