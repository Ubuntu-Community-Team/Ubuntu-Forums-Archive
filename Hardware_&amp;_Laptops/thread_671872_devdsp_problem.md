---
title: "/dev/dsp problem"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by karusho on 2008-01-19
Hello,

I was playing around with eSpeak, and it was working great, until something crashed Compiz (and some other things, I don't know, but I had to redo the SKIP_CHECKS = yes thing again) and I ended up using Ctrl+Alt+Backspace to kill X.

When everything came back, using eSpeak produced this:
```
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

```

---

### Post by karusho on 2008-01-21
*bumpers*

Is this really such rare of an error?  Or have I posted this in the wrong forum?

---

### Post by nidelius on 2008-02-18
I had the same problem 

```
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
```


I realized that it was GizmoProject that locked down the sound device. So when I shutdown gizmo it worked fine.

Probably some program locked or are locking down your audio device

---

### Post by ghjf345 on 2008-02-27
I had the same problem, and I found an answer here
[http://www.usenet-forums.com/linux-general/98834-locking-sharing-dev-dsp.html](http://www.usenet-forums.com/linux-general/98834-locking-sharing-dev-dsp.html)

---

