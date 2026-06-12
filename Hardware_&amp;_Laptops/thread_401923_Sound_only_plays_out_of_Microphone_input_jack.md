---
title: "Sound only plays out of Microphone input jack"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by sligocki on 2007-04-05
I installed Ubuntu a few days ago (installed Breezy and upgraded -> Dapper -> Edgy) on my Gateway laptop and I'm not getting any sound coming out of the speakers.  Interestingly, if I plug my headphones into the microphone input jack, the correct audio comes out!?

Most of the help that I found on this site explains how to try and install the correct drivers if Ubuntu failed to find them automatically.  However, it seems to me that I do have the correct drivers (as the correct audio is output), just with the wrong configurations.  But this is just a guess.

Here is some info from my computer:
Model: **Gateway M675 Laptop (2004)**
[http://support.gateway.com/s/Mobile/Gateway/M675/3501731nv.shtml]("http://support.gateway.com/s/Mobile/Gateway/M675/3501731nv.shtml")
A specification can be found here: [http://support.gateway.com/s/Mobile/Gateway/M675/8510002.pdf]("http://support.gateway.com/s/Mobile/Gateway/M675/8510002.pdf")

Under **Processor and Core Logic** it says that the **Chipset** is:
```
Intel 82865PE + Intel 82801EB (ICH5)
```
Under **Audio** it says that the **Audio Chipset** is:
```
Sigmatel® Soft Audio 6-channel AC97 rev 2.3 codec (STAC9758)
```


"lspci | grep audio" gives:
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```

"tail -2 /proc/asound/oss/sndstat" gives:
```
Mixers:
0: SigmaTel STAC9758,59
```

I have included full output from:
1. aadebug
2. /proc/asound/oss/sndstat

Do you guys know what I can try to get it working?
Let me know if there's any more information that would help.

Thanks,
-Shawn

---

### Post by ddaedalus on 2007-04-05
IIRC these are known bugs in ALSA. You can try to compile your own ALSA. [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by sligocki on 2007-04-05
Actually, after looking around a little I saw a post suggesting trying the command (alsamixer).  After poking around for a few minutes I discovered that setting **Center/LFE Jack** to **Mixer Output** worked.

I don' t know why any of this worked and my other jacks (Like headphone, microphone, etc.) still don't work.  So if anyone has any suggestions on how to set this up intelligently that'd be nice.  But thanks for the reply.

Also, thanks to cyberdork33  [http://ubuntuforums.org/showpost.php?p=2361135&postcount=5]("http://ubuntuforums.org/showpost.php?p=2361135&postcount=5") for the comment that I used to get it working.

-Shawn

---

