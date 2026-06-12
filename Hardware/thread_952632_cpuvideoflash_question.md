---
title: "cpu/video/flash question"
date: 2008-10-19
forum: Hardware
---

### Post by jon.reeve on 2008-10-19
I have two laptops, 

1. A 2.0 GHz P4, with an ATI Radeon Mobility M6LY video card and 1G memory, and

2. a 1.6 GHz MSI Wind, also with 1G RAM. 

What I don't quite understand is, why the 2.0 GHz machine gets really choppy video on Hulu and other sites with flash video, and does all this with the CPU at 100%, while the 1.6 GHz machine plays flash video perfectly, even at full screen, and the CPU is barely even at 50%. 

Does this sound like it's a problem with flash, compiz, xorg, video drivers, hardware, or some crazy combination of all of them?

---

### Post by king.pest on 2008-10-19
are you using ati propertiary drivers on your 2.0 GHz machine? because it may be a problem with some hardware acceleration not present by default.

---

### Post by jon.reeve on 2008-10-19
The proprietary drivers don't support my particular ATI card, unfortunately.

---

### Post by king.pest on 2008-10-20
hmm... i just tried to search for some solution and i see, that your card is supported by the opensource "radeon" driver (same as a radeon in my thinkpad). are you using it? if not, there's an old howto about it [here]("http://ubuntuforums.org/showthread.php?t=246746").

---

### Post by jon.reeve on 2008-10-20
Yep, that's the one I'm using. I followed many of the instructions I gleaned from that thread, too, and the fastest configuration I could come up with still only gets me 200-some frames in glxgears and a generally choppy playback of all video.

---

