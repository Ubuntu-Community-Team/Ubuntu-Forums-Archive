---
title: "Problem with ffmpeg and aac audio?"
date: 2005-11-14
forum: General Help
---

### Post by glib on 2005-11-14
First post here, umm... hi.

So I'm trying to convert a video for use on a new ipod (and starting to consider writing a script to simplify things a bit). I've used ffmpeg to do it with other distros (gentoo and arch), but when I try it with ubuntu, it complains about the aac audio I want. Tried to download and compile from cvs with the needed --enable-faad flag (why it wasn't compiled with this in the first place is beyond me... people would still have the option of not installing libfaad if they really wanted to save the disc space). After realizing there's no make or gcc by default, I sorta got things going. Problem is that there's no gcc executable, so I just linked the gcc-3.4 one that the package installed to gcc and hoped that would work? Didn't seem to. Found out about the 'build-essentials' package, and that got me a step further. Still no go though. Gets stuck looking for a 'dts.h' file that's probably part of some package I don't have installed.

Why oh why must it be so difficult to convert a video for my ipod.

---

### Post by reedlaw on 2005-11-14
Have you tried this:
```
sudo apt-get install gstreamer0.8-faac gstreamer0.8-faad
```

---

### Post by Iandefor on 2005-11-14
I feel your pain! Linux can be fairly difficult sometimes. 
 I would suggest giving a little more detail; what is the format of the video you are trying to convert? and the desired format?
 Some research indicates that ffmpeg requires both faad and faac to work. Both of these are available through Synaptic. Enable the [Multiverse repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto"). Go to a terminal and type in ```
sudo aptitude install libfaad2-0 libfaac0 
``` and they should be installed. Hopefully, that helped a little.

---

### Post by glib on 2005-11-15
Thanks for the efforts, but I've already got all of those installed. The problem is that ffmpeg *would* work with libfaac *if* it was compiled with the '--enable-faac' flag, but for some reason it wasn't. I'd really like to know why, but barring that, I'd like to know how to compile my own version.

```
$ ./configure --help | grep aac
  --enable-faac            enable FAAC support via libfaac [default=no]
```

```
ffmpeg -i input.avi -b 800 -vcodec mpeg4 -ab 128 -acodec aac output.mp4
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, avi, from 'input.avi':
  Duration: 00:48:18.7, start: 0.000000, bitrate: 1013 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x336, 23.98 fps
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 96 kb/s
Unknown codec 'aac'
```

Compile error:
```
gcc -O3  -DHAVE_AV_CONFIG_H -I.. -I'/home/glib/Desktop/ffmpeg'/libavutil -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE    -c -o liba52/crc.o liba52/crc.c
gcc -O3  -DHAVE_AV_CONFIG_H -I.. -I'/home/glib/Desktop/ffmpeg'/libavutil -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE    -c -o liba52/resample.o liba52/resample.c
gcc -O3  -DHAVE_AV_CONFIG_H -I.. -I'/home/glib/Desktop/ffmpeg'/libavutil -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE    -c -o dtsdec.o dtsdec.c
dtsdec.c:27:17: error: dts.h: No such file or directory
dtsdec.c:60: error: syntax error before &#8216;*&#8217; token
dtsdec.c: In function &#8216;convert2s16_2&#8217;:
dtsdec.c:63: error: &#8216;_f&#8217; undeclared (first use in this function)
dtsdec.c:63: error: (Each undeclared identifier is reported only once
dtsdec.c:63: error: for each function it appears in.)
dtsdec.c:67: error: &#8216;s16&#8217; undeclared (first use in this function)
dtsdec.c: At top level:
dtsdec.c:73: error: syntax error before &#8216;*&#8217; token
dtsdec.c: In function &#8216;convert2s16_4&#8217;:
dtsdec.c:76: error: &#8216;_f&#8217; undeclared (first use in this function)
dtsdec.c:80: error: &#8216;s16&#8217; undeclared (first use in this function)
dtsdec.c: At top level:
dtsdec.c:88: error: syntax error before &#8216;*&#8217; token
dtsdec.c: In function &#8216;convert2s16_5&#8217;:
dtsdec.c:91: error: &#8216;_f&#8217; undeclared (first use in this function)
dtsdec.c:95: error: &#8216;s16&#8217; undeclared (first use in this function)
dtsdec.c: At top level:
dtsdec.c:104: error: syntax error before &#8216;*&#8217; token
dtsdec.c: In function &#8216;convert2s16_multi&#8217;:
dtsdec.c:107: error: &#8216;_f&#8217; undeclared (first use in this function)
dtsdec.c:109: error: &#8216;flags&#8217; undeclared (first use in this function)
dtsdec.c:111: error: &#8216;DTS_MONO&#8217; undeclared (first use in this function)
dtsdec.c:114: error: &#8216;s16&#8217; undeclared (first use in this function)
dtsdec.c:118: error: &#8216;DTS_CHANNEL&#8217; undeclared (first use in this function)
dtsdec.c:119: error: &#8216;DTS_STEREO&#8217; undeclared (first use in this function)
dtsdec.c:120: error: &#8216;DTS_DOLBY&#8217; undeclared (first use in this function)
dtsdec.c:123: error: &#8216;DTS_3F&#8217; undeclared (first use in this function)
dtsdec.c:132: error: &#8216;DTS_2F2R&#8217; undeclared (first use in this function)
dtsdec.c:135: error: &#8216;DTS_3F2R&#8217; undeclared (first use in this function)
dtsdec.c:138: error: &#8216;DTS_LFE&#8217; undeclared (first use in this function)
dtsdec.c: In function &#8216;channels_multi&#8217;:
dtsdec.c:195: error: &#8216;DTS_LFE&#8217; undeclared (first use in this function)
dtsdec.c:199: error: &#8216;DTS_CHANNEL_MASK&#8217; undeclared (first use in this function)
dtsdec.c:199: error: &#8216;DTS_2F2R&#8217; undeclared (first use in this function)
dtsdec.c: In function &#8216;dts_decode_frame&#8217;:
dtsdec.c:220: error: &#8216;dts_state_t&#8217; undeclared (first use in this function)
dtsdec.c:220: error: &#8216;state&#8217; undeclared (first use in this function)
dtsdec.c:253: error: &#8216;level_t&#8217; undeclared (first use in this function)
dtsdec.c:253: error: syntax error before &#8216;level&#8217;
dtsdec.c:254: error: &#8216;sample_t&#8217; undeclared (first use in this function)
dtsdec.c:258: error: &#8216;level&#8217; undeclared (first use in this function)
dtsdec.c:259: error: &#8216;bias&#8217; undeclared (first use in this function)
dtsdec.c:261: error: &#8216;DTS_ADJUST_LEVEL&#8217; undeclared (first use in this function)
dtsdec.c:275: error: &#8216;DTS_CHANNEL_MASK&#8217; undeclared (first use in this function)
dtsdec.c:275: error: &#8216;DTS_LFE&#8217; undeclared (first use in this function)
dtsdec.c: In function &#8216;dts_decode_init&#8217;:
dtsdec.c:298: warning: assignment makes pointer from integer without a cast
dtsdec.c: At top level:
dtsdec.c:315: error: &#8216;dts_state_t&#8217; undeclared here (not in a function)
dtsdec.c:315: error: syntax error before &#8216;)&#8217; token
make[1]: *** [dtsdec.o] Error 1
make[1]: Leaving directory `/home/glib/Desktop/ffmpeg/libavcodec'
make: *** [lib] Error 2
```

---

### Post by glib on 2005-11-15
Got it to compile.

This will drag in the necessary deps to compile:
```
sudo apt-get build-dep ffmpeg
```

I used the --enable-faac flag, and the compile died on me once complaining about faad stuff, so I installed libfaad-dev, then it did the same about faac and was solved again by installing libfaac-dev. No problems after that. Happily converting video for my ipod.

---

