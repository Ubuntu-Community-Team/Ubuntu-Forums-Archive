---
title: "MP4 player problem"
date: 2011-02-19
forum: Hardware
---

### Post by JFekete9076 on 2011-02-19
Hello.

I got an portable MP4 player from a friend. He told me that some video files can't play in it.
He gave me some papers about the files' details. According to them, I've realised that the device only supports videos with XVID MPEG4 video and MP1 audio codecs, and some videos aren't coded in these formats.

I want to know how to change these videos' audio codec to MP1 (I know how to change the video codec using FFmpeg).

Best regards.

---

### Post by JFekete9076 on 2011-03-13
Here's my attempt:
```

jfekete@jfekete-GA-MA770T-UD3:~/Desktop$ ffmpeg -i input.avi -vcodec mpeg4 -vtag xvid -acodec mp1 output.avi
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:35:47 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'input.avi':
  Metadata:
    ISFT            : MEncoder Sherpya-SVN-r30075-4.2.5
  Duration: 00:03:16.44, start: 0.000000, bitrate: 645 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 32 kb/s
Unknown encoder 'mp1'

```

---

### Post by FakeOutdoorsman on 2011-03-13
MP1? Really? What device is this? As far as I know FFmpeg does not have a MP1 encoder.
```
$ ffmpeg -codecs | grep -i MP1
 D..... = Decoding supported
 ..A... = Audio codec
 D A    mp1             MP1 (MPEG audio layer 1)
 D A    mp1float        MP1 (MPEG audio layer 1)
```
Do you have a video that does work with this device? You can probe it with FFmpeg for details:
```
ffmpeg -i input.foo
```

---

### Post by JFekete9076 on 2011-03-14
```
ffmjfekete@jfekete-GA-MA770T-UD3:~/Desktop$ ffmpeg -i input2.avi
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:35:47 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'input2.avi':
  Metadata:
    ISFT            : Lavf52.54.0
  Duration: 00:00:20.55, start: 0.000000, bitrate: 570 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, 2 channels, s16, 128 kb/s
At least one output file must be specified

```

I see. It seems to be mp2, not mp1.
Thank you for your help.

---

### Post by JFekete9076 on 2011-03-14
I've attached a picture of the device.

---

### Post by JFekete9076 on 2011-03-14
It doesn't work. I've tried to convert the file to MPEG4 with and without the XVID tag, and MP2 as audio codec.

---

### Post by FakeOutdoorsman on 2011-03-14
These devices can be picky to create a working video, but not impossible. You just have to make many test videos. [mediainfo](http://mediainfo.sourceforge.net/en/Download) may show more useful information about the video that does work.

---

### Post by SeijiSensei on 2011-03-14
Are you sure the output file isn't larger than the maximum resolution of the device?  I've had to rescale videos to make them fit the 480x272 px display resolution on my COWON A2.  

I've had success re-encoding with [mencoder]("http://en.gentoo-wiki.com/wiki/Mencoder") like this 

```
mencoder -o output.avi -oac mp3lame -ovc xvid -xvidencopts=pass=1  input.mkv
```

This does a quick (one-pass) conversion to XviD and MP3.  In this case, the input is a Matroska file, but it could be nearly anything.  For two-pass methods, and other details, see the linked document.

---

### Post by JFekete9076 on 2011-03-14
> **SeijiSensei said:**
> Are you sure the output file isn't larger than the maximum resolution of the device?  I've had to rescale videos to make them fit the 480x272 px display resolution on my COWON A2.  

I've had success re-encoding with [mencoder]("http://en.gentoo-wiki.com/wiki/Mencoder") like this 

```
mencoder -o output.avi -oac mp3lame -ovc xvid -xvidencopts=pass=1  input.mkv
```This does a quick (one-pass) conversion to XviD and MP3.  In this case, the input is a Matroska file, but it could be nearly anything.  For two-pass methods, and other details, see the linked document.

One video has proper resolution, another not.

By the way, I gave it a try:
```
jfekete@jfekete-GA-MA770T-UD3:~/Desktop$ mencoder -o output.avi -oac mp3lame -ovc xvid input.avi
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 0  data: 0x0 - 0xf1ab86
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  320x240  12bpp  25.000 fps  509.2 kbps (62.2 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:320x240  fps:25.000  ftime:=0.0400
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
xvid: using library version 1.2.2 (build xvid-1.2.2)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
MP3 audio selected.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: XviD (320x240 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=320x240, sampled=320x240
xvid: you must specify one or a valid combination of 'bitrate', 'pass', 'fixed_quant' settings
FATAL: Cannot initialize video driver.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: XviD (320x240 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=320x240, sampled=320x240
xvid: you must specify one or a valid combination of 'bitrate', 'pass', 'fixed_quant' settings
FATAL: Cannot initialize video driver.

Exiting...

```

---

### Post by SeijiSensei on 2011-03-14
You need -xvidencopts, and I made an error in my original posting.   It should read:

```
mencoder -o output.avi -oac mp3lame -ovc xvid -xvidencopts pass=1 input.avi
```

without the equals sign after xvidencopts that I had before. (I haven't done this for a while now.)  Make sure xvidencopts comes after -ovc xvid.

This will produce a file with MP3 audio, assuming you have all the codecs.  If you need MP2, you'll have to use libavcodec instead.  Then you'd have:

```
mencoder -o output.avi -ovc xvid -xvidencopts pass=1 -oac lavc -lavcopts acodec=mp2:abitrate=224 input.avi
```

or something like that.  See the manual I linked to earlier details, or the official [Mencoder Manual]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html").

You can see what codecs you have installed with "mencoder -ovc help" and "mencoder -oac help".  (Same method works with mplayer, using "-vo help" and "-ao help" instead.)  I don't what codecs come with the version in the Ubuntu repositories.  I always build mplayer/mencoder from [source]("http://www.mplayerhq.hu/MPlayer/releases/mplayer-export-snapshot.tar.bz2").

---

### Post by JFekete9076 on 2011-03-15
Here is a comparison of a working and a not-working video:[ http://www.mediafire.com/i/?gsz55zyusfzgm8r]("http://www.mediafire.com/i/?gsz55zyusfzgm8r")

---

### Post by JFekete9076 on 2011-04-06
Could someone help me with solving this problem?
The owner of the device can't wait to get it back.

---

### Post by FakeOutdoorsman on 2011-04-06
Your working file uses MP2 audio, while the non-working one has MP3 audio. A close approximation of the working video may be:
```
ffmpeg -i input -vcodec libxvid -r 25 -b 416k -s 320x240 -acodec mp2 -ab 128k -ar 44100 -ac 2 output.avi
```

---

