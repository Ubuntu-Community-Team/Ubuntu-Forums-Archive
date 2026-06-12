---
title: "My built-in microphone wont work- Medion MD 96582"
date: 2010-04-26
forum: Hardware
---

### Post by chicabomb on 2010-04-26
Hi, 

as you figured it out my mic wont work, sound works perfectly but it still wont work, with this post im sending you my configurations in hope that will help you figure it out what could possibly be wrong...

my ubuntu version is 9.10

the funniest part is that my soundcard wasnt found but in this 9.10 and 7.04 now that i do have sound my microphone wont work

hope to hear from someone soon

almir@almir-laptop:~$ uname -a
Linux almir-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
almir@almir-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
almir@almir-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
almir@almir-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC888

---

### Post by randumbtune on 2010-05-02
same Issue, It never worked for any linux that ive installed on my Laptop, 

one of the major reasons of why I had to move to windows

---

