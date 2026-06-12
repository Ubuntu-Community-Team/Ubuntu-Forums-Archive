---
title: "Crackle Audio, especially after advertising additional to video"
date: 2023-09-20
forum: Hardware
---

### Post by gloster10 on 2023-09-20
Ubuntu 22.04 (but also Linux Mint has the same behaviour), AMD RX560, audio via HDMI.

The crackle sometimes can be stopped after logout/login, it is not immediately after starting the Internet video play, sometimes after 1h, sometimes after 5min.

Is there a possibility to save the respective audio output to HDMI via a layer reference, to check which layer will be involved ?

---

### Post by TheFu on 2023-09-22
x-discontinuity issue. [https://github.com/jellyfin/jellyfin-ffmpeg/issues/57](https://github.com/jellyfin/jellyfin-ffmpeg/issues/57)

There are workarounds if you compile ffmpeg manually (with the x-discontinuity hack that breaks other things) or use an analog hole.

But violating the terms of use for Crackle would be against UF rules.

---

