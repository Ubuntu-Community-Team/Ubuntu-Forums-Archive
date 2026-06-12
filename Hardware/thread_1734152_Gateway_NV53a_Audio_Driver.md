---
title: "Gateway NV53a Audio Driver"
date: 2011-04-19
forum: Hardware
---

### Post by darthveggie on 2011-04-19
Hi! My girlfriend just installed Ubuntu 10.10 64-bit to her Gateway NV53a notebook and has had a pretty good experience so far. Her biggest trouble is that her Realtek audio driver doesn't come up, and the Device Manager doesn't show anything about it at all. Could anyone please help me find it and/or find a generic driver that would work? 

She says that she has sound, but it's all screwed up. Her laptop doesn't recognize any audio hardware that is plugged into it. When she was running Windows 7, however, the sound was fine, so her sound card isn't broken. Any help at all would be greatly appreciated! :)

---

### Post by lidex on 2011-04-21
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

