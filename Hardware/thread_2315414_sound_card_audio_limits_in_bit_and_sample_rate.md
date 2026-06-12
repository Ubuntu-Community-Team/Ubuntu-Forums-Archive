---
title: "sound card audio limits in bit and sample rate"
date: 2016-02-28
forum: Hardware
---

### Post by Robert_Gaines on 2016-02-28
I would like to find out how high my sound card can play and record audio in bit and sample rate. (Ex. 16bit at 44.1kHz, 32bit at 96kHz) Is there like a command line utility that can display this information?

---

### Post by dave157 on 2016-02-28
Hi there

Have a look at this post

[http://askubuntu.com/questions/19212/how-do-i-know-if-my-system-is-capable-of-playing-24bit-96khz-sound](http://askubuntu.com/questions/19212/how-do-i-know-if-my-system-is-capable-of-playing-24bit-96khz-sound)

:D

---

### Post by Robert_Gaines on 2016-02-29
Okay, the example wasn't precisely what I needed, but I was able to look location directly and get the correct syntax pattern for it. Here's some examples for those who may need it.

The original example is: ```
cat /proc/asound/card0/codec#2
```
My HDMI is: ```
cat /proc/asound/card0/codec#0
```
My analog in/out is: ```
cat /proc/asound/card1/codec#1
```

That should do it. Thanks! :) I can't figure out how to mark this as "solved". I'll check my profile...

---

