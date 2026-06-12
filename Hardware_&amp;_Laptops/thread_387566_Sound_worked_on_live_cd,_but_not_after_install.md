---
title: "Sound worked on live cd, but not after install"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by wcampbell on 2007-03-18
I'm relatively new to linux, have played with a few different distros, and I really like ubuntu.  I recently installed on a Dell GX150.  When I ran the install from the live CD, I had sound, but now I do not.  I'm not sure whether it was the updates that messed things up or if it just didnt work after the install.

The device manager shows '82801BA/BAM AC'97 Audio' with about 8 things below it like 'I82801BA-CH2 ASLA Control Device',I82801BA-CH2 ASLA playback device', etc.

I'm not really good with command line syntax yet, but I can certainly follow directions, something like "what does the output from blahblah" wont mean much to me unless you can tell me how to produce that output.

Any help would really be appreciated.

Thanks!
Warren

---

### Post by AtrejuT on 2007-03-18
First I'd check if something is muted for some reason. In a terminal type
```

alsamixer

```

and see what it looks like, i.e. are the equalizer bars of master and pcm somewhere that seems reasonable and is there a green OO at the bottom of both these bars?

---

### Post by wcampbell on 2007-03-18
Master and Master Mono are both at around 85% and have the 00.

PCM is does not have 00.  At the top, under 'item' for PCM it says 'PCM (OFF)'.   I can move the level up and down with the arrow keys, but I cant figure out how to turn it on.

---

### Post by wcampbell on 2007-03-18
also, I just turned the Master all the way down, and it went to OFF.  When I bring it back up, the level goes up, but it still says off.

---

### Post by wcampbell on 2007-03-18
Figured it out... the M key.

Thanks!

---

