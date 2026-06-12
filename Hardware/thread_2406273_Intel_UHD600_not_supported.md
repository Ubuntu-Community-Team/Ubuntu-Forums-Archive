---
title: "Intel UHD600 not supported"
date: 2018-11-18
forum: Hardware
---

### Post by juancarlos.castro on 2018-11-18
Hi all


First of all, to thank the community for helping those we do not know.

My problem is that my computer (Intel N4100 with UHD600) the graphic card is not recognized by default by lubuntu 18.04.1 LTS.
[https://ark.intel.com/products/128983/Intel-Celeron-N4100-Processor-4M-Cache-up-to-2-40-GHz-](https://ark.intel.com/products/128983/Intel-Celeron-N4100-Processor-4M-Cache-up-to-2-40-GHz-)

I have tried with mesa drivers, and then if it recognizes it, but it does not use VA API


I'm using Emby to a home server, and in Windows it can transcodificate perfectly. But with lubuntu 18.04 and 18.10 it don't work.
I've first addressed the problem in the emby forum, thinking that the problem was with their software.
[https://emby.media/community/index.php?/topic/13029-ubuntu/?p=648125](https://emby.media/community/index.php?/topic/13029-ubuntu/?p=648125)

If i find information about intel drivers, theoretically Gemini lake is supported
[https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe](https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe)

I have tried all the kernels, drivers, ffmpeg, etc ... and the GPU is never used to transcode

On the emby post I have put a lot of information, but if I need to put it back here

I'll be waiting for your answers
THANKS

---

### Post by Yellow Pasque on 2018-11-18
Pleas give some basic info to begin:
```
glxinfo -B
vainfo
ffmpeg -hwaccels
```

---

### Post by juancarlos.castro on 2018-11-18
Hi,

In this moment, I am using Mesa drivers

> 
home-server@home-server:~$ glxinfo -B
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel Open Source Technology Center (0x8086)
    Device: Mesa DRI Intel(R) UHD Graphics 600 (Geminilake 2x6)  (0x3185)
    Version: 18.2.2
    Accelerated: yes
    Video memory: 3072MB
    Unified memory: yes
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) UHD Graphics 600 (Geminilake 2x6) 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 18.2.2
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile


OpenGL version string: 3.0 Mesa 18.2.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)


OpenGL ES profile version string: OpenGL ES 3.2 Mesa 18.2.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20


> 
home-server@home-server:~$ vainfo
libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_1_1
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.1 (libva 2.1.0)
vainfo: Driver version: Intel i965 driver for Intel(R) Gemini Lake - 2.1.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSliceLP
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointEncSliceLP
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointEncSliceLP
      VAProfileH264MultiviewHigh      :    VAEntrypointVLD
      VAProfileH264MultiviewHigh      :    VAEntrypointEncSlice
      VAProfileH264StereoHigh         :    VAEntrypointVLD
      VAProfileH264StereoHigh         :    VAEntrypointEncSlice
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
      VAProfileJPEGBaseline           :    VAEntrypointVLD
      VAProfileJPEGBaseline           :    VAEntrypointEncPicture
      VAProfileVP8Version0_3          :    VAEntrypointVLD
      VAProfileVP8Version0_3          :    VAEntrypointEncSlice
      VAProfileHEVCMain               :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointEncSlice
      VAProfileHEVCMain10             :    VAEntrypointVLD
      VAProfileHEVCMain10             :    VAEntrypointEncSlice
      VAProfileVP9Profile0            :    VAEntrypointVLD
      VAProfileVP9Profile0            :    VAEntrypointEncSlice
      VAProfileVP9Profile2            :    VAEntrypointVLD


> 
home-server@home-server:~$ ffmpeg -hwaccels
ffmpeg version 4.0.3-1~18.04.york0 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version='1~18.04.york0' --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      56. 14.100 / 56. 14.100
  libavcodec     58. 18.100 / 58. 18.100
  libavformat    58. 12.100 / 58. 12.100
  libavdevice    58.  3.100 / 58.  3.100
  libavfilter     7. 16.100 /  7. 16.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  1.100 /  5.  1.100
  libswresample   3.  1.100 /  3.  1.100
  libpostproc    55.  1.100 / 55.  1.100
Hardware acceleration methods:
vdpau
vaapi
drm



Now I will try installed this driver:
[https://www.archlinux.org/packages/community/x86_64/intel-media-driver/](https://www.archlinux.org/packages/community/x86_64/intel-media-driver/)


Thanks

---

### Post by Yellow Pasque on 2018-11-18
```
Hardware acceleration methods:
vdpau
vaapi
drm
```

There is no support for Intel QuickSync video in your version of ffmpeg ("qsv" should have appeared in this list). I believe that is the problem, but I'm not familiar with Emby. Does it use the system's ffmpeg for transcoding?

> Now I will try installed this driver:
[https://www.archlinux.org/packages/c...-media-driver/](https://www.archlinux.org/packages/c...-media-driver/)


Please don't. This is packaged for Arch Linux. The driver is likely not your issue. 'glxinfo' and 'vainfo' output looks good.

---

### Post by juancarlos.castro on 2018-11-18
if necessary, I have no problem in formatting the system and start from 0

---

### Post by juancarlos.castro on 2018-11-18
> **Temüjin said:**
> ```
Hardware acceleration methods:
vdpau
vaapi
drm
```

There is no support for Intel QuickSync video in your version of ffmpeg ("qsv" should have appeared in this list). I believe that is the problem, but I'm not familiar with Emby. Does it use the system's ffmpeg for transcoding?



Please don't. This is packaged for Arch Linux. The driver is likely not your issue. 'glxinfo' and 'vainfo' output looks good.
Yes, this is the capture
[IMG]https://emby.media/community/uploads/inline/339606/5beb10430d07b_Sinttulo.jpg[/IMG]

I know QSV is not supported from intel since 17.04. For this you have to use VAAPI in linux, and theoretically if it is supported.

These are two tests that I was asked in the emby forum
> home-server@home-server:~/Vídeos$ ffmpeg -i '001.mkv' -s 1280x720 -f null -

ffmpeg version 4.0.3-1~18.04.york0 Copyright © 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version='1~18.04.york0' --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      56. 14.100 / 56. 14.100
  libavcodec     58. 18.100 / 58. 18.100
  libavformat    58. 12.100 / 58. 12.100
  libavdevice    58.  3.100 / 58.  3.100
  libavfilter     7. 16.100 /  7. 16.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  1.100 /  5.  1.100
  libswresample   3.  1.100 /  3.  1.100
  libpostproc    55.  1.100 / 55.  1.100
Input #0, matroska,webm, from '001.mkv':
  Metadata:
    encoder         : libebml v1.3.6 + libmatroska v1.4.9
    creation_time   : 2018-09-17T19:00:02.000000Z
  Duration: 00:41:10.76, start: 0.000000, bitrate: 2078 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 704x396 [SAR 1:1 DAR 16:9], 25 fps, 25 tbr, 1k tbn, 23.98 tbc (default)
    Metadata:
      BPS-eng         : 1692668
      DURATION-eng    : 00:41:10.760000000
      NUMBER_OF_FRAMES-eng: 61769
      NUMBER_OF_BYTES-eng: 522772108
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
    Stream #0:1(spa): Audio: mp3, 48000 Hz, stereo, fltp, 192 kb/s (default)
    Metadata:
      BPS-eng         : 192000
      DURATION-eng    : 00:41:10.752000000
      NUMBER_OF_FRAMES-eng: 102948
      NUMBER_OF_BYTES-eng: 59298048
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
    Stream #0:2(eng): Audio: mp3, 48000 Hz, stereo, fltp, 192 kb/s
    Metadata:
      BPS-eng         : 192000
      DURATION-eng    : 00:41:10.752000000
      NUMBER_OF_FRAMES-eng: 102948
      NUMBER_OF_BYTES-eng: 59298048
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg4 (native) -> wrapped_avframe (native))
  Stream #0:1 -> #0:1 (mp3 (mp3float) -> pcm_s16le (native))
Press [q] to stop, [?] for help
Output #0, null, to 'pipe:':
  Metadata:
    encoder         : Lavf58.12.100
    Stream #0:0: Video: wrapped_avframe, yuv420p, 1280x720 [SAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 25 fps, 25 tbn, 25 tbc (default)
    Metadata:
      BPS-eng         : 1692668
      DURATION-eng    : 00:41:10.760000000
      NUMBER_OF_FRAMES-eng: 61769
      NUMBER_OF_BYTES-eng: 522772108
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
      encoder         : Lavc58.18.100 wrapped_avframe
    Stream #0:1(spa): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s (default)
    Metadata:
      BPS-eng         : 192000
      DURATION-eng    : 00:41:10.752000000
      NUMBER_OF_FRAMES-eng: 102948
      NUMBER_OF_BYTES-eng: 59298048
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
      encoder         : Lavc58.18.100 pcm_s16le
frame=35112 fps=337 q=-0.0 size=N/A time=00:23:24.79 bitrate=N/A speed=13.5x    
 



[IMG]https://emby.media/community/uploads/inline/339606/5bef463ff4183_01.jpg[/IMG]

> home-server@home-server:~/Vídeos$ ffmpeg -hwaccel vaapi -i '001.mkv' -s 1280x720 -f null -


ffmpeg version 4.0.3-1~18.04.york0 Copyright © 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version='1~18.04.york0' --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      56. 14.100 / 56. 14.100
  libavcodec     58. 18.100 / 58. 18.100
  libavformat    58. 12.100 / 58. 12.100
  libavdevice    58.  3.100 / 58.  3.100
  libavfilter     7. 16.100 /  7. 16.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  1.100 /  5.  1.100
  libswresample   3.  1.100 /  3.  1.100
  libpostproc    55.  1.100 / 55.  1.100
Input #0, matroska,webm, from '001.mkv':
  Metadata:
    encoder         : libebml v1.3.6 + libmatroska v1.4.9
    creation_time   : 2018-09-17T19:00:02.000000Z
  Duration: 00:41:10.76, start: 0.000000, bitrate: 2078 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 704x396 [SAR 1:1 DAR 16:9], 25 fps, 25 tbr, 1k tbn, 23.98 tbc (default)
    Metadata:
      BPS-eng         : 1692668
      DURATION-eng    : 00:41:10.760000000
      NUMBER_OF_FRAMES-eng: 61769
      NUMBER_OF_BYTES-eng: 522772108
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
    Stream #0:1(spa): Audio: mp3, 48000 Hz, stereo, fltp, 192 kb/s (default)
    Metadata:
      BPS-eng         : 192000
      DURATION-eng    : 00:41:10.752000000
      NUMBER_OF_FRAMES-eng: 102948
      NUMBER_OF_BYTES-eng: 59298048
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
    Stream #0:2(eng): Audio: mp3, 48000 Hz, stereo, fltp, 192 kb/s
    Metadata:
      BPS-eng         : 192000
      DURATION-eng    : 00:41:10.752000000
      NUMBER_OF_FRAMES-eng: 102948
      NUMBER_OF_BYTES-eng: 59298048
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg4 (native) -> wrapped_avframe (native))
  Stream #0:1 -> #0:1 (mp3 (mp3float) -> pcm_s16le (native))
Press [q] to stop, [?] for help
[mpeg4 @ 0x55f6e933f600] No support for codec mpeg4 profile 15.
[mpeg4 @ 0x55f6e933f600] Failed setup for format vaapi_vld: hwaccel initialisation returned error.
Output #0, null, to 'pipe:':
  Metadata:
    encoder         : Lavf58.12.100
    Stream #0:0: Video: wrapped_avframe, yuv420p, 1280x720 [SAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 25 fps, 25 tbn, 25 tbc (default)
    Metadata:
      BPS-eng         : 1692668
      DURATION-eng    : 00:41:10.760000000
      NUMBER_OF_FRAMES-eng: 61769
      NUMBER_OF_BYTES-eng: 522772108
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
      encoder         : Lavc58.18.100 wrapped_avframe
    Stream #0:1(spa): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s (default)
    Metadata:
      BPS-eng         : 192000
      DURATION-eng    : 00:41:10.752000000
      NUMBER_OF_FRAMES-eng: 102948
      NUMBER_OF_BYTES-eng: 59298048
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
      encoder         : Lavc58.18.100 pcm_s16le
frame=11584 fps=325 q=-0.0 size=N/A time=00:07:43.58 bitrate=N/A speed=  13x 

[IMG]https://emby.media/community/uploads/inline/339606/5bef4742039de_02.jpg[/IMG]

---

### Post by Yellow Pasque on 2018-11-18
> **juancarlos.castro said:**
> if necessary, I have no problem in formatting the system and start from 0

I don't see any reason to reinstall. You mention that you have asked for help on Emby's site. Do you have a link? What advice did they give you there (if any)?

How did you install emby? It does not appear to be present in standard Ubuntu repositories.

---

### Post by juancarlos.castro on 2018-11-18
> **Temüjin said:**
> I don't see any reason to reinstall. You mention that you have asked for help on Emby's site. Do you have a link? What advice did they give you there (if any)?

How did you install emby? It does not appear to be present in standard Ubuntu repositories.
I only proposed it because I use the mesa drives, and not the i965 repository

I have downloaded the deb from your website and followed the instructions
[https://emby.media/linux-server.html](https://emby.media/linux-server.html)
dpkg -i emby-server-deb_3.5.3.0_amd64.deb

And this is where I've been talking about the problem.
In the end it was concluded that the problem is that the system does not use VAAPI
[https://emby.media/community/index.php?/topic/13029-ubuntu/?p=648125](https://emby.media/community/index.php?/topic/13029-ubuntu/?p=648125)

---

### Post by Yellow Pasque on 2018-11-18
> In the end it was concluded that the problem is that the system does not use VAAPI

Who concluded that? Your 'vainfo' output looks good. Ubuntu's version of ffmpeg is built with VA-API support. So I would guess that either Emby is not set to use VA-API, only works with QuickSync, or it uses an internal version of ffmpeg that does not support VA-API. It does not seem like a problem with Ubuntu to me. But I am not familiar with Emby and I don't own an Intel GPU system. So I won't claim to be an expert in either area.

---

### Post by juancarlos.castro on 2018-11-19
> **Temüjin said:**
> Who concluded that? Your 'vainfo' output looks good. Ubuntu's version of ffmpeg is built with VA-API support. So I would guess that either Emby is not set to use VA-API, only works with QuickSync, or it uses an internal version of ffmpeg that does not support VA-API. It does not seem like a problem with Ubuntu to me. But I am not familiar with Emby and I don't own an Intel GPU system. So I won't claim to be an expert in either area.
That conclusion was reached because using ffmpeg from the command line, the result is the same with or without -hwaccel vaap

See this probe:
[https://ubuntuforums.org/showthread.php?t=2406273&p=13817282#post13817282](https://ubuntuforums.org/showthread.php?t=2406273&p=13817282#post13817282)
> 
[COLOR=#000000]*ffmpeg -i '001.mkv' -s 1280x720 -f null -*[/COLOR]
[COLOR=#000000]*ffmpeg -hwaccel vaapi -i '001.mkv' -s 1280x720 -f null -*[/COLOR]


---

### Post by Yellow Pasque on 2018-11-19
> mpeg4 (Advanced Simple Profile) (XVID / 0x44495658)

Intel GPU's don't support any hardware acceleration (decoding or encoding) for the old XVID codec, so I would not expect to see any difference using -hwaccel when decoding an xvid file. You should try that experiment with a different file that is supported with hardware decode (like a video using H.264/AVC or H.265/HEVC codec).

> I only proposed it because I use the mesa drives, and not the i965 repository

You are getting confused with terminology. 
'mesa' refers to the 3D driver: ```
Device: Mesa DRI Intel(R) UHD Graphics 600 (Geminilake 2x6) (0x3185)
```
'i965' refers to the VA-API driver: ```
vainfo: Driver version: Intel i965 driver for Intel(R) Gemini Lake - 2.1.0
```
Again, these outputs are good. I would not try to install different video drivers.

---

### Post by juancarlos.castro on 2018-11-19
> **Temüjin said:**
> Intel GPU's don't support any hardware acceleration (decoding or encoding) for the old XVID codec, so I would not expect to see any difference using -hwaccel when decoding an xvid file. You should try that experiment with a different file that is supported with hardware decode (like a video using H.264/AVC or H.265/HEVC codec).



You are getting confused with terminology. 
'mesa' refers to the 3D driver: ```
Device: Mesa DRI Intel(R) UHD Graphics 600 (Geminilake 2x6) (0x3185)
```
'i965' refers to the VA-API driver: ```
vainfo: Driver version: Intel i965 driver for Intel(R) Gemini Lake - 2.1.0
```
Again, these outputs are good. I would not try to install different video drivers.
Hello again,


I do not want to take the opposite since I'm not understood, but I think the Gemini Lake series does have support.
Also, in windows if it worked
[IMG]https://emby.media/community/uploads/inline/339606/5bed805d41aa8_GPUon.jpg[/IMG]

This file is the same of 001.mkv.

Then, you can see the UHD600 can transcode (obviously on windows using IntelQuickSync)
[https://en.wikichip.org/wiki/intel/uhd_graphics/600](https://en.wikichip.org/wiki/intel/uhd_graphics/600)

And remenber the "standard" installation don't recognice the graphic card, although the intel driver is installed by default[IMG]https://emby.media/community/uploads/inline/339606/5beda161155af_01.jpg[/IMG]

Regards

---

### Post by sfatula on 2018-11-19
Linux should be using vappi, not Quicksync directly. I believe it supports acceleration, this site says it does, as does your other test.

[https://www.notebookcheck.net/Intel-UHD-Graphics-600-GPU.271820.0.html](https://www.notebookcheck.net/Intel-UHD-Graphics-600-GPU.271820.0.html)

It is not well supported in software yet I don't think based on various changelogs I had read.

I'd be curious if you installed Windows on the same machine, would it use it. Not saying to keep Windows of course, just curious if a quick test can be done. I thought your example in the other forum with Windows working was a different machine? Maybe I remember wrong now. I may be confused about that.

Definitely don't install archlinux stuff. 

I still expect the UHD 600 to potentially support acceleration based on everything I have read. The question is why ffmpeg (which Emby does use for transcoding) does not use it. It does appear that is is there. And base ubuntu ffmpeg does support vaapi.

Have you tried the ffmpeg test with an H.264 file? Emby needs to be kept on the sideline until we see if ffmpeg will transcode with acceleration. If it will not, then, Emby becomes irrelevant as it won't work.

---

### Post by juancarlos.castro on 2018-11-19
I bought this equipment, which comes with Windows:
[http://www.bee-link.com/Beelink-MiniPC-TV-BOX-108-1.html](http://www.bee-link.com/Beelink-MiniPC-TV-BOX-108-1.html)

I have used emby on windows if problems with transcoding

Now, I need to use linux to be able to use other applications, and that's when I find this problem.
The computer is always the same.

---

### Post by Yellow Pasque on 2018-11-19
> And remenber the "standard" installation don't recognize the graphic card
```
sudo update-pciids
``` 
^Run that and see if it helps the  "Informacion del sistema" GUI

---

### Post by juancarlos.castro on 2018-11-22
> **Temüjin said:**
> ```
sudo update-pciids
``` 
^Run that and see if it helps the  "Informacion del sistema" GUI
I've tried with Ubuntu 18.10 and 19.05 (beta), and the same thing always happens.
I have already returned to Lubuntu 18.04.1

I just finished the installation, I just installed vainfo.

> home-server@home-server:~$ sudo update-pciids
Downloaded daily snapshot dated 2018-11-21 03:15:02




---

### Post by Yellow Pasque on 2018-11-23
We seem to be going around in circles. The bottom line is that your system is correctly setup to use VA-API acceleration with ffmpeg. You need to be looking at your Emby settings and I suggest pursuing help on Emby forums with people who are familiar with Emby, for best results.

---

### Post by juancarlos.castro on 2018-11-23
Hi,

But if I use ffmpeg directly from the command line, it does not work either.But..... I thing discovered something

```
home-server@home-server:~/Vídeos$ ffmpeg -version
ffmpeg version 4.0.3-1~18.04.york0 Copyright (c) 2000-2018 the FFmpeg developers
built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
configuration: --prefix=/usr --extra-version='1~18.04.york0' --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
libavutil      56. 14.100 / 56. 14.100
libavcodec     58. 18.100 / 58. 18.100
libavformat    58. 12.100 / 58. 12.100
libavdevice    58.  3.100 / 58.  3.100
libavfilter     7. 16.100 /  7. 16.100
libavresample   4.  0.  0 /  4.  0.  0
libswscale      5.  1.100 /  5.  1.100
libswresample   3.  1.100 /  3.  1.100
libpostproc    55.  1.100 / 55.  1.100

```

```

home-server@home-server:~/Vídeos$ ffmpeg -hwaccels
ffmpeg version 4.0.3-1~18.04.york0 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version='1~18.04.york0' --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      56. 14.100 / 56. 14.100
  libavcodec     58. 18.100 / 58. 18.100
  libavformat    58. 12.100 / 58. 12.100
  libavdevice    58.  3.100 / 58.  3.100
  libavfilter     7. 16.100 /  7. 16.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  1.100 /  5.  1.100
  libswresample   3.  1.100 /  3.  1.100
  libpostproc    55.  1.100 / 55.  1.100
Hardware acceleration methods:
vdpau
vaapi
drm



```

```

home-server@home-server:~/Vídeos$ vainfo
libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_1_1
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.1 (libva 2.1.0)
vainfo: Driver version: Intel i965 driver for Intel(R) Gemini Lake - 2.1.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSliceLP
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointEncSliceLP
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointEncSliceLP
      VAProfileH264MultiviewHigh      :    VAEntrypointVLD
      VAProfileH264MultiviewHigh      :    VAEntrypointEncSlice
      VAProfileH264StereoHigh         :    VAEntrypointVLD
      VAProfileH264StereoHigh         :    VAEntrypointEncSlice
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
      VAProfileJPEGBaseline           :    VAEntrypointVLD
      VAProfileJPEGBaseline           :    VAEntrypointEncPicture
      VAProfileVP8Version0_3          :    VAEntrypointVLD
      VAProfileVP8Version0_3          :    VAEntrypointEncSlice
      VAProfileHEVCMain               :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointEncSlice
      VAProfileHEVCMain10             :    VAEntrypointVLD
      VAProfileHEVCMain10             :    VAEntrypointEncSlice
      VAProfileVP9Profile0            :    VAEntrypointVLD
      VAProfileVP9Profile0            :    VAEntrypointEncSlice
      VAProfileVP9Profile2            :    VAEntrypointVLD

```


Then, I try transcode 3 diferents videos:
```

home-server@home-server:~/Vídeos$ ffmpeg -hwaccel vaapi -i '001.avi' -s 1280x720 -f null -
ffmpeg version 4.0.3-1~18.04.york0 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version='1~18.04.york0' --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      56. 14.100 / 56. 14.100
  libavcodec     58. 18.100 / 58. 18.100
  libavformat    58. 12.100 / 58. 12.100
  libavdevice    58.  3.100 / 58.  3.100
  libavfilter     7. 16.100 /  7. 16.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  1.100 /  5.  1.100
  libswresample   3.  1.100 /  3.  1.100
  libpostproc    55.  1.100 / 55.  1.100
[mpeg4 @ 0x55b470a6a640] Failed to parse extradata
Input #0, avi, from '001.avi':
  Metadata:
    encoder         : Lavf56.40.101
  Duration: 00:59:13.07, start: 0.000000, bitrate: 1334 kb/s
    Stream #0:0: Video: mpeg4 (Simple Profile) (XVID / 0x44495658), yuv420p, 720x406 [SAR 255:254 DAR 45900:25781], 1194 kb/s, SAR 406:405 DAR 16:9, 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 44100 Hz, stereo, fltp, 128 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg4 (native) -> wrapped_avframe (native))
  Stream #0:1 -> #0:1 (mp3 (mp3float) -> pcm_s16le (native))
Press [q] to stop, [?] for help
**[mpeg4 @ 0x55b470aad700] No support for codec mpeg4 profile 0.**
**[mpeg4 @ 0x55b470aad700] Failed setup for format vaapi_vld: hwaccel initialisation returned error.**
Output #0, null, to 'pipe:':
  Metadata:
    encoder         : Lavf58.12.100
    Stream #0:0: Video: wrapped_avframe, yuv420p, 1280x720 [SAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 25 fps, 25 tbn, 25 tbc
    Metadata:
      encoder         : Lavc58.18.100 wrapped_avframe
    Stream #0:1: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
    Metadata:
      encoder         : Lavc58.18.100 pcm_s16le
frame= 1106 fps=418 q=-0.0 Lsize=N/A time=00:00:44.40 bitrate=N/A speed=16.8x    
video:579kB audio:7650kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: unknown
Exiting normally, received signal 2.

```

```

home-server@home-server:~/Vídeos$ ffmpeg -hwaccel vaapi -i '002.mkv' -s 1280x720 -f null -
ffmpeg version 4.0.3-1~18.04.york0 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version='1~18.04.york0' --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      56. 14.100 / 56. 14.100
  libavcodec     58. 18.100 / 58. 18.100
  libavformat    58. 12.100 / 58. 12.100
  libavdevice    58.  3.100 / 58.  3.100
  libavfilter     7. 16.100 /  7. 16.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  1.100 /  5.  1.100
  libswresample   3.  1.100 /  3.  1.100
  libpostproc    55.  1.100 / 55.  1.100
Input #0, matroska,webm, from '002.mkv':
  Metadata:
    encoder         : libebml v1.3.6 + libmatroska v1.4.9
    creation_time   : 2018-09-17T19:00:02.000000Z
  Duration: 00:41:10.76, start: 0.000000, bitrate: 2078 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 704x396 [SAR 1:1 DAR 16:9], 25 fps, 25 tbr, 1k tbn, 23.98 tbc (default)
    Metadata:
      BPS-eng         : 1692668
      DURATION-eng    : 00:41:10.760000000
      NUMBER_OF_FRAMES-eng: 61769
      NUMBER_OF_BYTES-eng: 522772108
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
    Stream #0:1(spa): Audio: mp3, 48000 Hz, stereo, fltp, 192 kb/s (default)
    Metadata:
      BPS-eng         : 192000
      DURATION-eng    : 00:41:10.752000000
      NUMBER_OF_FRAMES-eng: 102948
      NUMBER_OF_BYTES-eng: 59298048
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
    Stream #0:2(eng): Audio: mp3, 48000 Hz, stereo, fltp, 192 kb/s
    Metadata:
      BPS-eng         : 192000
      DURATION-eng    : 00:41:10.752000000
      NUMBER_OF_FRAMES-eng: 102948
      NUMBER_OF_BYTES-eng: 59298048
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg4 (native) -> wrapped_avframe (native))
  Stream #0:1 -> #0:1 (mp3 (mp3float) -> pcm_s16le (native))
Press [q] to stop, [?] for help
**[mpeg4 @ 0x55e55bb97600] No support for codec mpeg4 profile 15.**
**[mpeg4 @ 0x55e55bb97600] Failed setup for format vaapi_vld: hwaccel initialisation returned error.**
Output #0, null, to 'pipe:':
  Metadata:
    encoder         : Lavf58.12.100
    Stream #0:0: Video: wrapped_avframe, yuv420p, 1280x720 [SAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 25 fps, 25 tbn, 25 tbc (default)
    Metadata:
      BPS-eng         : 1692668
      DURATION-eng    : 00:41:10.760000000
      NUMBER_OF_FRAMES-eng: 61769
      NUMBER_OF_BYTES-eng: 522772108
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
      encoder         : Lavc58.18.100 wrapped_avframe
    Stream #0:1(spa): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s (default)
    Metadata:
      BPS-eng         : 192000
      DURATION-eng    : 00:41:10.752000000
      NUMBER_OF_FRAMES-eng: 102948
      NUMBER_OF_BYTES-eng: 59298048
      _STATISTICS_WRITING_APP-eng: mkvmerge v26.0.0 ('In The Game') 64-bit
      _STATISTICS_WRITING_DATE_UTC-eng: 2018-09-17 19:00:02
      _STATISTICS_TAGS-eng: BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES
      encoder         : Lavc58.18.100 pcm_s16le
frame= 1132 fps=424 q=-0.0 Lsize=N/A time=00:00:45.45 bitrate=N/A speed=  17x    
video:593kB audio:8523kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: unknown
Exiting normally, received signal 2.

```

```

home-server@home-server:~/Vídeos$ ffmpeg -hwaccel vaapi -i '003.avi' -s 1280x720 -f null -
ffmpeg version 4.0.3-1~18.04.york0 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-27ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version='1~18.04.york0' --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      56. 14.100 / 56. 14.100
  libavcodec     58. 18.100 / 58. 18.100
  libavformat    58. 12.100 / 58. 12.100
  libavdevice    58.  3.100 / 58.  3.100
  libavfilter     7. 16.100 /  7. 16.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  1.100 /  5.  1.100
  libswresample   3.  1.100 /  3.  1.100
  libpostproc    55.  1.100 / 55.  1.100
Input #0, avi, from '003.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.10.2 (build 2540/release)
  Duration: 01:25:02.88, start: 0.000000, bitrate: 1608 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 704x400 [SAR 1:1 DAR 44:25], 1438 kb/s, 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, stereo, fltp, 160 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg4 (native) -> wrapped_avframe (native))
  Stream #0:1 -> #0:1 (mp3 (mp3float) -> pcm_s16le (native))
Press [q] to stop, [?] for help
**[mpeg4 @ 0x55d67e9391c0] No support for codec mpeg4 profile 15.**
**[mpeg4 @ 0x55d67e9391c0] Failed setup for format vaapi_vld: hwaccel initialisation returned error.**
Output #0, null, to 'pipe:':
  Metadata:
    encoder         : Lavf58.12.100
    Stream #0:0: Video: wrapped_avframe, yuv420p, 1280x720 [SAR 99:100 DAR 44:25], q=2-31, 200 kb/s, 25 fps, 25 tbn, 25 tbc
    Metadata:
      encoder         : Lavc58.18.100 wrapped_avframe
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
    Metadata:
      encoder         : Lavc58.18.100 pcm_s16le
frame=  963 fps=298 q=-0.0 Lsize=N/A time=00:00:39.19 bitrate=N/A speed=12.1x    
video:504kB audio:7348kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: unknown
Exiting normally, received signal 2.

```


But if I play the same videos with gnome-mpv, it use the hardware acceleration.
Does this give you some information?

Regards

---

