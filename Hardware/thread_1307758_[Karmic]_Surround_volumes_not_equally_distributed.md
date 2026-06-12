---
title: "[Karmic] Surround volumes not equally distributed"
date: 2009-10-31
forum: Hardware
---

### Post by mojo2012 on 2009-10-31
Hi guys,

HW specs:
OS: Ubuntu 9.10, 32-bit
Motherboard: ASUS A8N SLI-Deluxe
Soundcard: Nvidia CH804/ALC885
System/Preference/Audio Settings: Analog Surround 4.1 Output + Analog Stereo Input

Stereo is working fine, but surround gives me trouble (the same in jaunty ...). If I turn the sound volume to the lowest level, the front volume (called master in alsamixer) is very low, but the rear volume (called surround in alsamixer) is at ~80%. If I then turn the the volume slider even further down, both front and rear  get muted.

If I turn the volume slider up, only front gets louder until it reaches about 20%, then suddenly the rear volume goes up to 100%.

LFE and Master are somewhat linked together. PCM acts nearly the same way as Surround, but its volumes doesn't get that high.

I tried to change the device settings to 5.1, 7.1 and all the other possible values. But most of them give me scratchy sound and some (even more) weird volume problems.

To sum it up: sound is working on all speakers, but the volume gain is unequally distributed among the speakers. First to surround speakers are too lound. At a certain volume level, they don't get any louder any more, but the front is too loud instead.

In Jaunty I finally managed to make the volume slider work correctly, by selecting those "output lines" (eg, master, front, rear) that should be adjusted by the volume slider. But in Karmic this preference applet is gone.

So any idea, how to make this work as it should?

If you need any logs or whatever, just say it! 

####################
aplay -l:
ash@Odin:/var/log$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: CK804 [NVidia CK804], Gerät 0: Intel ICH [NVidia CK804]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: CK804 [NVidia CK804], Gerät 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
ash@Odin:/var/log$

---

### Post by mojo2012 on 2009-11-02
Nobody? Does anybody of you just have any clue or experience with this problem?
I search many forums and didn't find anything useful. I tried so many hints - edit config files or install additional apps, but couldn't resolve the problem.

---

### Post by kjwein on 2009-11-06
I had a similar problem to the one you are describing. This thread helped me fix it, hopefully it does the same for you. [http://ubuntuforums.org/showthread.php?p=8261235&posted=1#post8261235](http://ubuntuforums.org/showthread.php?p=8261235&posted=1#post8261235)

---

### Post by mojo2012 on 2009-11-07
Thanx man, this solved my problem. But sound is now much lower. Is there a way to boost the overall volume?

Without your hint I would have never ever thought about looking for an equalizer to solve my problem!

---

### Post by kjwein on 2009-11-08
I'm glad I helped solve part of your problem, but I am not sure how to fix the new one. I'm new to Ubuntu and still don't really know what I am doing. Good luck though!

---

