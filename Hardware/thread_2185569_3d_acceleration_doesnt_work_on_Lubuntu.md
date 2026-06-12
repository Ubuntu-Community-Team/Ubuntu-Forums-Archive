---
title: "3d acceleration doesnt work on Lubuntu"
date: 2013-11-03
forum: Hardware
---

### Post by 4dr14n on 2013-11-03
Hello all,

I have a problem on my Lubuntu 13.04, and that is that when I play videos my video card doesnt work properly, but it's like single frames, there is no continuity between the pics. 
I have read something about on the net and it seems to be a problem with the 3D acceleration.
I put my controller:
VGA compatible controller		: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon Xpress 1200/1250/1270] 

Thank you

---

### Post by Yellow Pasque on 2013-11-03
3D acceleration has nothing to do with it. The problem is that the video card doesn't support UVD ( [https://en.wikipedia.org/wiki/Unified_Video_Decoder#UVD_enabled_GPUs](https://en.wikipedia.org/wiki/Unified_Video_Decoder#UVD_enabled_GPUs) ) and everything is being done on your CPU, which is apparently too slow to play whatever you're trying to play.

---

### Post by 4dr14n on 2013-11-03
Makes sense... the laptop has already few years. I hate doing this kind of questions but I'm quite nob and I don't know what to do with the info you gave; and my card is not in the list.

Thank you again.

---

### Post by Yellow Pasque on 2013-11-03
> **4dr14n said:**
> I don't know what to do with the info you gave; and my card is not in the list.

In your case, there's nothing to do except get better hardware or view videos at lower resolutions...

---

