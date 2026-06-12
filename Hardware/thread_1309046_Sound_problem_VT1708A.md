---
title: "Sound problem VT1708A"
date: 2009-11-01
forum: Hardware
---

### Post by loghete on 2009-11-01
Hello!
I just did a clean install of Ubuntu 9.10 on my laptop (replacing Vista), and most things are working fine except from the sound. I get sound from the internal speakers but none from the headphone jack. I am sure I've unmuted all channels, and the headphone jack worked fine on Vista.
Here are results from an lspci:

```
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
```The sound card is recognised and visible in the sound manager, but at some point, not sure what triggers it, the sound card disappears from that list and internal speakers stop working. After restarting the system the speakers work again but the headphone jack remains silent.

Any ideas?
Thanks.

---

### Post by ceinueng on 2009-11-11
I got exactly the same problem as stated above. Tried googling for solutions but still no hope yet. For the meantime, I can only use only playback audio system such as playing movie or audio file but not the recording function.;)

---

### Post by ceinueng on 2009-11-18
My problem is solved by:
1. Upgrading Alsa Driver from 1.0.20 to 1.0.21 [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
2. Fix mic vol setting by running alsamixer command line via terminal [http://ubuntuforums.org/showthread.php?t=1298047](http://ubuntuforums.org/showthread.php?t=1298047)
3. Adjust mic vol in Audacity program

Now I can use Audacity to record my voice practicing English pronunciation.

---

