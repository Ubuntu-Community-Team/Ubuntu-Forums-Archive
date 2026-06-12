---
title: "Compaq CQ57 - VLC - slow 1080p playback"
date: 2012-08-01
forum: Hardware
---

### Post by 1204 on 2012-08-01
[SIZE=1]Ubuntu 12.04 AMD64: E-300, 4GB, HD6310[/SIZE]

Well video plays two frames and stops, but video goes on and sound works perfectly. File is .mp4 and maybe H.264.  I guess it's using only processor not graphics card. AMD Catalyst 12.4 driver is installed. I've checked Catalyst settings. What else should I do? Is it related to [UVD]("http://en.wikipedia.org/wiki/Unified_Video_Decoder#UVD_enabled_GPUs")?

****** solve *******
[https://bugs.launchpad.net/ubuntu/+source/libva/+bug/974205](https://bugs.launchpad.net/ubuntu/+source/libva/+bug/974205)
> My Ubuntu 12.04 running on HP Probook 6465b is also affected. I  managed  to sort of fix it and get HW accelerated playback in VLC and  mplayer by  manualy putting "fglrx_drv_video.so" in  /usr/lib/x86_64-linux-gnu/dri/. I took it from the package  xvba-video_0.8.0-1_amd64.deb. HW accelerated playback is confirmed by  vainfo and lower cpu usage.


---

### Post by QIII on 2012-08-01
When you initialized the driver, did you do```
sudo aticonfig --adapter=all --initial
```
to make sure you initialized both the APU and the discrete card?  CCC should then allow you to switch between integrated and discrete graphics, but a logout/in is required.  This does not occur dynamically as in Windows.

Please see the ATI driver wiki in my signature.  There is a section in the table of contents entitled "Using the Ubuntu repositories (alternate command line method, including hardware acceleration" that may be helpful.

---

### Post by 1204 on 2012-08-01
Yeah I did that but not helped. Also fglrxinfo was ok. But hey, *va-driver* looks promising
```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```
```
sudo vainfo
```

---

### Post by QIII on 2012-08-01
UVD 2 and forward should not be an issue.

mp4 acceleration is not included in the hardware acceleration for ATI in Linux, IIRC.

I use smplayer, by the way.  I'm not happy with the quality using VLC.

---

### Post by 1204 on 2012-08-01
Yeah now it shows same *vainfo* as in ubuntu wiki. In vlc there is GPU acceleration enabled. But video doesn't play properly and it's same in other video players. It also doesn't play well HD flash videos on Youtube. Any suggestions?

Edit. I also tried original ubuntu fglrx drivers but those were worse than AMD Catalyst.

---

### Post by QIII on 2012-08-01
Flash is a problem.  Adobe chose to support hardware acceleration only for nVIDIA (VDPAU) so you are left with the APU/CPU for Flash with ATI.

Are you still only getting a few frames?  What happens if you switch to discrete?

BTW, the fglrx driver in the repo is the ATI driver, version 12.4, development branch 8.960.

If you installed fglrx-updates, that is problematic for some users.

---

### Post by 1204 on 2012-08-01
> **QIII said:**
> Flash is a problem.  Adobe chose to support hardware acceleration only for nVIDIA (VDPAU) so you are left with the APU/CPU for flash.Yeah but all videos on Youtube/VLC works better on my 5 year old Intel x3100/Celeron so I guess this is a GPU driver problem.
> Are you still only getting a few frames?  What happens if you switch to discrete?Yeah only couple frames and it stops. If you choose different point it plays a few frames and stops. Sounds works perfectly. 480p mkv/x264 file works well.

---

### Post by 1204 on 2012-08-01
> **QIII said:**
> BTW, the fglrx driver in the repo is the ATI driver, version 12.4, development branch 8.960.I also tried 12.6 but there was watermark that gpu is not supported (hd 6310). I installed 12.4 this way [>link<]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29")
```
sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
```

---

### Post by QIII on 2012-08-01
> **1204 said:**
> Yeah but all videos on Youtube/VLC works better on my 5 year old Intel x3100/Celeron so I guess this is a GPU driver problem.

I don't think so.  Flash dumps to the CPU with ATI graphics.  That was Adobe's decision.

> Yeah only couple frames and it stops. If you choose different point it plays a few frames and stops. Sounds works perfectly. 480p mkv/x264 file works well.

I'll have to look at VLC.  Somewhere there is a setting (rendering, maybe) that says something like "Fast, for ATI".

This may not be a driver problem per se.   In that case I'd expect playback, but just crappy playback.  I've never encountered what you are describing.  I'll have to do a bit of research.

---

### Post by 1204 on 2012-08-01
This post was not related to topic, so deleted not to mix readers in this case. Thank you QIII for your help and time. :)

---

### Post by 1204 on 2012-08-01
Post if you know any ati configs or anything, I'll test and tell results. Could this help in this case - what does it mean? From [http://forum.xbmc.org/showthread.php?tid=116996](http://forum.xbmc.org/showthread.php?tid=116996)
```
sudo aticonfig --set-pcs-u32=MCIL,HWUVD_H264Level51Support,1
```

---

### Post by QIII on 2012-08-02
I don't think you need to worry about that.

Could you start VLC from the terminal 

```
gksudo vlc
```

should do it.

When it stops after a few frames, take a look at the output in the terminal.  Are there any errors reported?

---

### Post by 1204 on 2012-08-02
Quake Live worked like a charm. Videos still doesn't work very well, I've tried everything said before. SMPlayer was like 0.5x speed and VLC just lags. System is E-300 not E-450. Here are the vlc and (S)mplayer logs
```
$ vlc
VLC media player 2.0.1 Twoflower (revision 2.0.1-0-gf432547)
[0x610108] main libvlc
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
xvba_video: XVBA_GetSurface(): status 2
``````
$ mplayer
Playing 123.mp4.
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [H264]  1920x1080  24bpp  30.000 fps  19966.0 kbps (2437.3 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: mp423gp4isomavc1
 creation_time: 2012-07-15 06:32:31
Load subtitles in ./
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.4 kbit/8.36% (ratio: 16051->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
A:   5.3 V:   1.7 A-V:  3.623 ct:  0.033   0/  0 283%  9%  8.9% 50 0 


           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  10.2 V:  10.4 A-V: -0.170 ct:  0.694   0/  0 273%  6%  3.2% 95 0 

```[B]
[SIZE=4]SOLVE[/SIZE][/B]
[https://bugs.launchpad.net/ubuntu/+source/libva/+bug/974205](https://bugs.launchpad.net/ubuntu/+source/libva/+bug/974205)
> My Ubuntu 12.04 running on HP Probook 6465b is also affected. I managed  to sort of fix it and get HW accelerated playback in VLC and mplayer by  manualy putting "fglrx_drv_video.so" in /usr/lib/x86_64-linux-gnu/dri/. I took it from the package xvba-video_0.8.0-1_amd64.deb. HW accelerated playback is confirmed by vainfo and lower cpu usage.


---

