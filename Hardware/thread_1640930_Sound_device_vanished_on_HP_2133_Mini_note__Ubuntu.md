---
title: "Sound device vanished on HP 2133 Mini note / Ubuntu 10.04"
date: 2010-12-08
forum: Hardware
---

### Post by treunanen on 2010-12-08
Hi,

I stumbled on a rather strange issue with my HP 2133 MiniNote equipped with Ubuntu 10.04. I attempted to use Skype to see if the webcam works or not and while I was at it I made a test call. The voice of the "instructor" lady came through fine until it was my part to see if my Microphone actually worked or not. I blappered a while and when the playback was supposed to come, I heard nothing.

So I started to check if I had it muted for some reason. So I went to System -> Preferences -> Sound and realized that under "Hardware" tab I had no devices listed, same thing on Input and under Output I had only "Dummy Output - Stereo".

I read from [https://wiki.edubuntu.org/LaptopTestingTeam/HP2133](https://wiki.edubuntu.org/LaptopTestingTeam/HP2133) that this might happen with the older alsa drivers, so I did the upgrade to 1.0.23, but nothing changed, I still have no audio devices:

```
~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Dec  8 2010 for kernel 2.6.32-26-generic (SMP).
```

```
~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any ideas on what might cause this is highly appreciated!

---

### Post by treunanen on 2010-12-12
I got this case fixed now with the instructions in here:

[http://ubuntuforums.org/showpost.php?p=10081788&postcount=37](http://ubuntuforums.org/showpost.php?p=10081788&postcount=37)

Though I am still able to reproduce the behavior when running skype and performing the test call. Any ideas how to get rid of this problem?

---

