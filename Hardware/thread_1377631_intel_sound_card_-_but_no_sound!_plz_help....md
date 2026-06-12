---
title: "intel sound card - but no sound! plz help..."
date: 2010-01-10
forum: Hardware
---

### Post by mha2908 on 2010-01-10
hi, I have this laptop with ubuntu on it - works great, except for no sound. The output of lspci | grep audio:

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

```

how to get this to work? Do I need new drivers - if I do, then how and where to get them? Plz help...

---

### Post by ajgreeny on 2010-01-10
first thing to do is run alsamixer in terminal which will produce a terminal mixer application.  navigate it with cursor keys to move from slider to slider and raise and lower the sliders, M to mute/unmute and tab to move from Playback to Capture to All.

Make sure nothing you need is muted or set too low, then press esc to quit.

---

