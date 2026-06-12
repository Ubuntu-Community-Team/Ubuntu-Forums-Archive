---
title: "post your glxgears results"
date: 2008-11-09
forum: Hardware
---

### Post by ipburbank on 2008-11-09
restart, close all programs, go into a shell and type glxgears. Wait about a long time, and then copy and paste the results into a .txt file with some system info at the top. for example:

```
EVGA geforce9600,
quad core @ 3.6 ghz:


~$ glxgears
66465 frames in 5.0 seconds = 13284.016 FPS
66510 frames in 5.0 seconds = 13301.939 FPS
66611 frames in 5.0 seconds = 13313.152 FPS
```

When you are done attach it as a file so we can all see!

Anyhow, I thought this would be a cool stat to put out there, I am doing it because I'm getting a new graphics card and am hoping to see how it measures up (what I just posted is not the new one).

Now this system isn't perfect I know. Why? well it doesn't do a comprehensive test. What would make a perfect test? Well for one thing this doesn't tax vram, it uses cpu power to help generate the image, but only one core. If there is someone out there who can code this, please do! It could be something like starting by opening 64 instances of glxgears, recording the frame rate, then opening more instances, and recording the frame rate. Or you could start from scratch and make something really nice! In any case I can't find anything that does this, so if you can find/write a program that does this I would be extremely grateful.

---

### Post by wgrant on 2008-11-09
I would like to remind people that there was a good reason for glxgears to not show framerates unless the -iacknowledgethatthistoolisnotabenchmark option was passed. That reason still stands.

---

### Post by ipburbank on 2008-11-10
Indeed, this is why I had that note on the bottom. Is there a good GPU benchmarking program out there?

---

