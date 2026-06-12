---
title: "Sound volume very low after Karmic upgrade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Manslen on 2009-10-30
Hello,

I have an Intel-based sound card, here is its lspci output:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

After upgrading to Karmic I had no sound. The multimedia settings had two "HDA Intel" devices (analog & digital) that worked in Jaunty but fail to initialize in Karmic. 
I therefore opted to install pulseaudio. This restored sound, but volume is very low.

I used alsamixer to max the volume of the device, yet the sound is still extremely weak. Any ideas?

---

### Post by ell02 on 2009-10-30
[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

This thread helped me , once i got simultaneous output all was good. Good luck.

---

### Post by Manslen on 2009-10-30
Thanks,

I tried a whole bunch of things and a few resets. Now my native Intel HDA devices came back to life. Sadly, I can't retrace what exactly solved the problems, or if the extra two resets did the trick.

---

