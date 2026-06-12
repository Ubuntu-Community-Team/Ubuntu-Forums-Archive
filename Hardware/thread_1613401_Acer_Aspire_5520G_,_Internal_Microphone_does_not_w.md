---
title: "Acer Aspire 5520G , Internal Microphone does not work , and multimedia keys !"
date: 2010-11-04
forum: Hardware
---

### Post by mykeandrew on 2010-11-04
I have an acer aspire 5520G , my internal microphone does not work, i  have ubuntu linux 10.10 and here are the results from those 

uname -a
 commands Linux myke-Aspire-5520 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

aplay -l
 **** List of PLAYBACK Hardware Devices ****
 card 0: NVidia [HDA NVidia], device 0: ALC268 Analog [ALC268 Analog]
   Subdevices: 1/1
   Subdevice #0: subdevice #0

 cat /proc/asound/version
 Advanced Linux Sound Architecture Driver Version 1.0.23.
 
head -n 1 /proc/asound/card*/codec#*
 ==> /proc/asound/card0/codec#0 <==
 Codec: Realtek ALC268
 
 ==> /proc/asound/card0/codec#1 <==
 Codec: Conexant ID 2c06

I've seen a solution in "[B]Microphone does not work on 10.04 on Dell e6410"  i didn't try it !

[/B]The multimedia keys does not work ( play, next , prev , stop , and some of the Fs ) 

**By the way i am a noob !**

---

### Post by sp0 on 2010-12-29
I have the same issue. My microphone sounds all "robotic". 

```
uname -a
Linux portabuntu 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.

head -n 1 /proc/asound/card*/codec#*

*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC268

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

```

---

### Post by lidex on 2010-12-30
Have a look here:
[http://ubuntuforums.org/showthread.php?p=10297176#post10297176](http://ubuntuforums.org/showthread.php?p=10297176#post10297176)

---

