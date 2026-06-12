---
title: "ffmpeg encoding trouble"
date: 2008-11-25
forum: General Help
---

### Post by reader4 on 2008-11-25
Having trouble encoding images to a video using the exact same line of code I have always used, but now I get:

```
$ ffmpeg -r 2 -f image2 -i %03d.jpg test.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
Input #0, image2, from '%03d.jpg':
  Duration: 00:00:05.5, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, gray, 1192x598 [PAR 35:35 DAR 596:299],  2.00 tb(r)
Output #0, mp4, to 'test.mp4':
    Stream #0.0: Video: 0x0000, gray, 1192x598 [PAR 1:1 DAR 596:299], q=2-31, 200 kb/s,  2.00 tb(c)
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0
```

I also tried specifying '-vcodec mpeg4' but get an error
```
Unknown encoder 'mpeg4'
```

Trying MPG gets me a file with bitrate=0, even if I specify it explicitly as 25.  Something seems off, but I can't figure it out... I tried reinstalling from synaptic but without luck.  Advice?

---

