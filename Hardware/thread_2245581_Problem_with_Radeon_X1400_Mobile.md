---
title: "Problem with Radeon X1400 Mobile"
date: 2014-09-24
forum: Hardware
---

### Post by giorgio8 on 2014-09-24
Hi everyone. These days I had the following inconvenient: my old Asus Eee PC died due to a motherboard failure, so I put its hard disk with Ubuntu  12.04 installed into an old Acer with a ATI Radeon X1400 video card. At first glance the system looked perfect, exactly as if it was running on its original machine, but I started experiencing problems when I tried to play a video with Vlc. Indeed I got a black screen and the usage of the CPU suddenly rose to 100% and I was forced to halt the PC in order to prevent overheating. Since my Asus mounted the (in)famous GPU GMA3600 ([https://wiki.archlinux.org/index.php/Intel_GMA3600](https://wiki.archlinux.org/index.php/Intel_GMA3600)) I noticed this is exactly the same behaviour the GMA3600 had, worstened by the fact now I can't play videos in any way. Indeed I checked which driver the system was using:
```

lspci -nnk |grep VGA -A3 |grep driver 
    Kernel driver in use: radeon

```
so the system is using the correct driver, but when required it seems not to use it. If I try to play a random video with mplayer I get the following (I hope more interesting) error message:
```

mplayer VID_20120927_112536.mp4 
MPlayer UNKNOWN-4.6 (C) 2000-2013 MPlayer Team
Cannot test OS support for SSE, disabling to be safe.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing VID_20120927_112536.mp4.
libavformat version 55.7.100 (internal)
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  1280x720  24bpp  90000.000 fps  9929.5 kbps (1212.1 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 0
 compatible_brands: isom3gp4
 creation_time: 2012-09-27 09:26:08
Load subtitles in ./
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns -1
[vo_vaapi] vaInitialize(): unknown libva error
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 55.9.100 (internal)
AUDIO: 16000 Hz, 1 ch, floatle, 96.0 kbit/18.74% (ratio: 11996->64000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 16000Hz 1ch floatle (4 bytes per sample)
Video: no video
Starting playback...
A:  30.1 (30.1) of 30.5 (30.4)  2.0% 




Exiting... (End of file)

```

Does someone know how to get rid of such errors and make the system use its videocard?

Thank you!

---

