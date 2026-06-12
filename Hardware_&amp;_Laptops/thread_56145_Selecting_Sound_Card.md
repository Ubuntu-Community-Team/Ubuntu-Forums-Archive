---
title: "Selecting Sound Card"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by mikerobinson on 2005-08-11
I have two soundcards on my system. One is an integrated soundcard that pretty much sucks. The other is a SB Live Value. The only program that I can get my sound to work is XMMS because it allows me to select the device to use, which in this case is EMU10K1 (hw:1,0), although the default is the integrated one. 

When I run `alsamixer` it shows the card being VIA 82C686A/B rev50 (my integrated soundcard). How can I change this to my SB Live so that I can get the audio to work in other programs besides XMMS?


Thanks,

Mike

---

### Post by Copter on 2005-08-12
hi!

check [here](http://ubuntuforums.org/showthread.php?t=27186). it is a great 2 soundcards howto. i had the same problem as you (but with Audigy Player card).

to run 2nd soundcard mixer type
```

alsamixer -c1
```
-c1 is the 2nd card, -c0 (default) is the 1st one.

copter :]

---

