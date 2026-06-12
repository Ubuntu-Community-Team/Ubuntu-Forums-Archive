---
title: "ffmpeg  and mpeg2video"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by joe2012 on 2009-09-10
I am trying to convert a single avi file into a DVD image. So I ran the following:
```
 ffmpeg -i out.avi -y -target ntsc-dvd -sameq -aspect 16:9 out.mpg
```but this is the error I get:
```
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from 'out.avi':
  Duration: 01:30:32.47, start: 0.000000, bitrate: 1074 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x320 [PAR 1:1 DAR 9:4], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 32 kb/s
Unknown encoder 'mpeg2video'

```I am following instructions from [here]("http://www.cyberciti.biz/tips/howto-linux-create-video-dvds.html")

Anyone have any ideas? I figure that I'm missing the mpeg2video encoder, but I don't know how to get it

---

### Post by joe2012 on 2009-09-10
for anyone that's interested, this got it to work:

```
sudo aptitude install ~nlibav.+-unstripped.+
```

---

### Post by FakeOutdoorsman on 2009-09-11
I wrote a guide on enabling additional encoders in FFmpeg:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=786095)

---

