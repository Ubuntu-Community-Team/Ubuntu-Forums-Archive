---
title: "How to disable this."
date: 2009-09-28
forum: Hardware
---

### Post by zaduma on 2009-09-28
I have two sound modules loading at boot. I do not need my ATI HDMI sound, and it is infact causing some minor issues.

I'm not sure what to put in the blacklist file.

here is lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
I do not want to disable my video card. I want to disable my ATI Audio. How can I accomplish this?

---

### Post by nixscripter on 2009-10-03
You need to determine  the name of the driver. Try running [b]lsmod[b] and look for snd-something.

---

