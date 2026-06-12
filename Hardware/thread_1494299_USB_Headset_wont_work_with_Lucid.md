---
title: "USB Headset wont work with Lucid"
date: 2010-05-26
forum: Hardware
---

### Post by andyobdog on 2010-05-26
Hey there, I am new to Ubuntu and I've been trying to get better with using it. One thing I cannot get around is makeing my USB headset work. Sound goes perfectly through my speakers (I think my soundcard is AC883 not sure whether it's relavent or not), but I am getting nothing through my headset when I plug it in. I go into Pulseaudio volume controller. It should recognize the headset as a seperate card but nothing is there. Alsa is upgraded to the latest version 1.0.23 I believe. Gnome Alsa-mixer doesn't get it to work either. I've googled and googled and googled the issue but all fixes seem to be for older versions on linux so every things seems to be pretty different. 
 
Some help on this would be greatly apreciated!
 
Andrew

---

### Post by Revolutionary101 on 2010-05-26
I have not been able to get my USB microphones to work either. I eventually just got a microphone that works with my microphone jack.

---

### Post by andyobdog on 2010-05-26
Problem is, I need the headphone piece to work as well. I've tried the standard audio jack as well but with no luck either.

---

### Post by lidex on 2010-05-26
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by AintJoe on 2010-08-24
I know I'm not the same guy, but I am having the same issue. I've had these headphones for years, and this is the first time I've had a problem.

```

root@blackbox:~# uname -a
Linux blackbox 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
root@blackbox:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
root@blackbox:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
root@blackbox:~# head -n 1 /proc/asound/card*/codec#*
Codec: VIA VT1708B 8-Ch

```

---

### Post by lidex on 2010-08-25
> **AintJoe said:**
> I know I'm not the same guy, but I am having the same issue. I've had these headphones for years, and this is the first time I've had a problem.

```

root@blackbox:~# uname -a
Linux blackbox 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
root@blackbox:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
root@blackbox:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
root@blackbox:~# head -n 1 /proc/asound/card*/codec#*
Codec: VIA VT1708B 8-Ch

```

Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```

---

### Post by Symbioosi on 2011-02-06
I'm having the same problem. 10.04 is a "stable" "long term support" release. Is anyone (of the Ubuntu developers) planning to fix this?

Edit: Seems that 10.04.2 is released at 17th of this month. I wonder if this will be fixed.

> **What kind of changes are appropriate to make in a released version of Ubuntu?**

 We only update packages for specific types of changes: 

[LIST]
[*]Fixes for security vulnerabilities 
[*]Other high-impact bug fixes, for example those which cause data loss 
[*]Very conservative, unintrusive bug fixes with substantial benefit and very low risk
[/LIST]


[https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)
[https://wiki.ubuntu.com/TimeBasedReleases#What%20kind%20of%20changes%20are%20appropriate%20to%20make%20in%20a%20released%20version%20of%20Ubuntu?](https://wiki.ubuntu.com/TimeBasedReleases#What%20kind%20of%20changes%20are%20appropriate%20to%20make%20in%20a%20released%20version%20of%20Ubuntu?)

---

