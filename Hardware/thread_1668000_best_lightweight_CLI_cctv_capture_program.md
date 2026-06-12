---
title: "best lightweight CLI cctv capture program"
date: 2011-01-15
forum: Hardware
---

### Post by wardy277 on 2011-01-15
Hi I have an EasyCAP USB card ( ID 05e1:0408 Syntek Semiconductor Co., Ltd)

I have installed the drivers from [http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)  as instructed by [http://easycap.blogspot.com/p/installation.html](http://easycap.blogspot.com/p/installation.html). This was very easy and it works. 

What my plan is is to have a small CCTV camera system pushed through to the card and then saved to a file. I have all the hardware and drivers setup so not  just need to understand how to use something like ffmpeg to do the recording in the background of my pc. I can get vlc to do it but it opens the gui.

Ideally i dont want it to use much resources, and run entirely in the background. (is it possible to only record movement or is motion detection hardware?)

i have tried the ffmpeg code from the tutorial site abouve but it doesnt seem to work (i think the driver got updated so the device locations have changed.
```
mencoder tv:// -tv driver=v4l2:width=720:height=576:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:adevice=/dev/easysnd1:audiorate=48000:amode=1:forceaudio:immediatemode=0 -msglevel all=9 -ffourcc DX50 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:turbo:vbitrate=1200:keyint=15 -vf pp=lb,scale=640:480 -oac mp3lame -o test.avi
```

produces:
```
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
this_opt = option: ffourcc
Setting ffourcc=DX50
this_opt = option: ovc
Setting ovc=lavc
this_opt = option: lavcopts
Setting lavcopts=vcodec=mpeg4:mbd=2:turbo:vbitrate=1200:keyint=15
this_opt = option: vf
Checking vf=pp=lb,scale=640:480
this_opt = option: oac
Setting oac=mp3lame
this_opt = option: o
Setting o=test.avi
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Config pushed level is now 2
Config pushed level is now 3
Setting tv=driver=v4l2:width=720:height=576:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:adevice=/dev/easysnd1:audiorate=48000:amode=1:forceaudio:immediatemode=0
Setting vf=pp=lb,scale=640:480
get_path('fonts') -> '/home/xbmc/.mplayer/fonts'
STREAM: [tv] tv://
STREAM: Description: TV Input
STREAM: Author: Benjamin Zores, Albeu
STREAM: Comment: 
success: format: 9  data: 0x0 - 0x0
seek to 0x0
s->pos=0  newpos=0  new_bufpos=0  buflen=0  
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: video fd: /dev/easycap0: 3
Selected device: EasyCAP DC60
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Format UYVY   (16 bits, uyvy): Packed UYVY
 Format YUYV   (16 bits, yuy2): Packed YUY2
 Format RGB24  (24 bits, rgb24): RGB 24-bit
 Format RGB32  (32 bits, rgb32): RGBA
 Format BGR24  (24 bits, bgr24): BGR 24-bit
 Format BGR32  (32 bits, bgr32): BGRA
 Current format: UYVY
v4l2: set format: UYVY
v4l2: set input: 0
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected norm : pal
v4l2: set norm: PAL_BGHIN
v4l2: set width: 720
v4l2: set height: 576
Selected input hasn't got a tuner!
==> Found video stream: 0
v4l2: get format: UYVY
v4l2: get fps: 25.000000
v4l2: get width: 720
v4l2: get height: 576
Unable to open '/dev/easysnd1': No such file or directory
v4l2: set audio samplerate: 48000
Unable to open '/dev/easysnd1': No such file or directory
Unable to open '/dev/easysnd1': No such file or directory
v4l2: 0 frames successfully processed, 0 frames dropped.
v4l2: up to 0 video frames buffered.
DEMUXER: freeing TV demuxer at 0xf13210
DEMUXER: freeing sh_video at 0xf15120
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```


this is the code that works with vlc:
vlc -vvv v4l2:///dev/easycap0:width=720:height=576 :norm=pal :input-slave=alsa://plughw:1,0 --demux rawvideo --sout file/mp2v:movie.avi 2>vlc.err

---

### Post by rmt1947 on 2011-01-16
Hi,

If you use the command "cvlc" instead of "vlc" I think you can avoid the GUI opening.  You might need to install the package "vlc-nox", although I suppose this is usually installed automatically when vlc itself is installed.

For some reason ffmpeg doesn't work with version 0.9 of the driver, but your mencoder command should work if you change "/dev/easysnd1" to "plughw.1,0" like this:

```
mencoder tv:// -tv driver=v4l2:width=720:height=576:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:adevice=plughw.1,0:audiorate=48000:amode=1:forceaudio:immediatemode=0 -msglevel all=9 -ffourcc DX50 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:turbo:vbitrate=1200:keyint=15 -vf pp=lb,scale=640:480 -oac mp3lame -o test.avi
```

Mike

---

### Post by IcarusR on 2011-01-16
I think Motion could be what you are looking for.

[http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome]("http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome")

---

### Post by wardy277 on 2011-01-16
thanks for your help.

I have tried that. I have tried that mencoder command but get the following error:
```
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Config pushed level is now 2
Config pushed level is now 3
Setting tv=driver=v4l2:width=720:height=576:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:adevice=plughw.1,0:audiorate=48000:amode=1:forceaudio:immediatemode=0
Setting vf=pp=lb,scale=640:480
get_path('fonts') -> '/home/xbmc/.mplayer/fonts'
STREAM: [tv] tv://
STREAM: Description: TV Input
STREAM: Author: Benjamin Zores, Albeu
STREAM: Comment: 
success: format: 9  data: 0x0 - 0x0
seek to 0x0
s->pos=0  newpos=0  new_bufpos=0  buflen=0  
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: video fd: /dev/easycap0: 3
Selected device: EasyCAP DC60
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Format UYVY   (16 bits, uyvy): Packed UYVY
 Format YUYV   (16 bits, yuy2): Packed YUY2
 Format RGB24  (24 bits, rgb24): RGB 24-bit
 Format RGB32  (32 bits, rgb32): RGBA
 Format BGR24  (24 bits, bgr24): BGR 24-bit
 Format BGR32  (32 bits, bgr32): BGRA
 Current format: YUYV
v4l2: set format: UYVY
v4l2: set input: 0
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected norm : pal
v4l2: set norm: PAL_BGHIN
v4l2: set width: 720
v4l2: set height: 576
Selected input hasn't got a tuner!
==> Found video stream: 0
v4l2: get format: UYVY
v4l2: get fps: 25.000000
v4l2: get width: 720
v4l2: get height: 576
Unable to open 'plughw.1,0': No such file or directory
v4l2: set audio samplerate: 48000
Unable to open 'plughw.1,0': No such file or directory
Unable to open 'plughw.1,0': No such file or directory
v4l2: 0 frames successfully processed, 0 frames dropped.
v4l2: up to 0 video frames buffered.
DEMUXER: freeing TV demuxer at 0x16a61d0
DEMUXER: freeing sh_video at 0x16a80e0
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

```

I have installed motion and that seems great. It works straight away and the motion detection just works. It only outputs images though. I could setup a nightly script to convert them to a video using ffmpeg or somthing, but can motion directly save as a video or does that use quite a bit of CPU. 

I have also seen ZoneMinder, which looks impressive as its control panel is web based so i can view it from work, but this doesnt work out of the box. It has quite a few options for the video input settings and  does give any errors that i can see. Does anyone have any experience with ZoneMinder?

Thank you for your help

---

