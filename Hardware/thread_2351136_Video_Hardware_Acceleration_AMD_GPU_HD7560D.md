---
title: "Video Hardware Acceleration AMD GPU HD7560D"
date: 2017-01-31
forum: Hardware
---

### Post by myway.1 on 2017-01-31
Hello,

I am not able to get video hardware acceleration (decoding).

AMD A8 5500B APU (HD7560D integrated graphics)
Xubuntu 14.04.4
Xubuntu-restricted-extras
fglrx driver (I am using this rather than radeon driver because it renders Facebook website better)
mpv player

Any idea why I am having this problem and how to fix it? (There are some error messages in the mpv output below)

```
joe@joe-desktop:~$ vainfo
libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: Found init function __vaDriverInit_0_32
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.35 (libva 1.3.0)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
```

```
joe@joe-desktop:~$ mpv --hwdec=vaapi /media/joe/'Seagate Expansion Drive/TV/Antiques Roadshow/Antiques_Roadshow_20161001_1030.mpg'
Playing: /media/joe/Seagate Expansion Drive/TV/Antiques Roadshow/Antiques_Roadshow_20161001_1030.mpg
 (+) Video --vid=1 (mpeg2video)
 (+) Audio --aid=1 (ac3)
libEGL warning: DRI2: failed to authenticate
[vo/opengl] glGetString(GL_VERSION) returned NULL.
AO: [pulse] 48000Hz 5.1(side) 6ch float
Using software decoding.
VO: [opengl] 1920x1080 yuv420p
 (+) Video --vid=1 (mpeg2video)
 (+) Audio --aid=1 (ac3)
     Subs  --sid=1 (eia_608)
(Paused) AV: 00:00:02 / 00:29:39 (0%) A-V:  0.000 Cache: 10s+73MB

```

---

### Post by myway.1 on 2017-01-31
I did a fresh install of Lubuntu 14.04.1, installed fglrx and the other packages mentioned on the Ubuntu binary driver AMD howto webpage using cli and installed mpv ( which is an old version) from repository. Hardware acceleration worked. I then removed mpv and installed the current version of mpv. Hardware acceleration no longer works. 

Honestly I'm not sure VAAPI hardware acceleration is something I want to use anyway.

My issue is that I want to use a high quality deinterlacer for 1080i video playback. Yadif 2x bogs down my CPU but standard yadif works. I wonder if the deinterlacing done by vaapi is better than standard yadif? If not then I will stick with software deinterlacing.

---

