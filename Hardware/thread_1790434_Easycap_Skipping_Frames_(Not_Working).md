---
title: "Easycap Skipping Frames (Not Working)"
date: 2011-06-25
forum: Hardware
---

### Post by rizlmilk on 2011-06-25
I recently purchased an Easycap to see if I could get it to work in Linux. (It was less than $10)

I installed the drivers for it located on SourceForge. I had to go into recovery mode to get it installed because snd_usb_audio was being used and caused it to not install otherwise.

Now that the drivers are installed, I still can't seem to get it to work. For example, trying to record with mencoder results in an endless amount of skipped frames. Also, Cheese tries to do something with it, but it just shows the spinning "loading" image forever. Here is the terminal output for mencoder:

> ryan@ryan-desktop:~$ mencoder tv:// -tv device=/dev/video0:input=1:norm=1:width=640: height=480 -vf pp=md -o Recording -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: EasyCAP DC60
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Current format: UYVY
tv.c: norm_from_string(1): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
[V] filefmt:9  fourcc:0x59565955  size:640x480  fps:25.000  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed UYVY)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed UYVY as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
    Last message repeated 1 times
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xc79020]BICUBIC scaler, from uyvy422 to yuv420p using MMX2
[swscaler @ 0xc79020]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xc79020]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xc79020]using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xc79020]640x480 -> 640x480
videocodec: libavcodec (640x480 fourcc=34504d46 [FMP4])
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.

Skipping frame!
Pos:   0.0s      1f ( 0%)  0.95fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      2f ( 0%)  1.27fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      3f ( 0%)  1.43fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      4f ( 0%)  1.52fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      5f ( 0%)  1.59fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      6f ( 0%)  1.63fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      7f ( 0%)  1.67fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      8f ( 0%)  1.69fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      9f ( 0%)  1.71fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     10f ( 0%)  1.73fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     11f ( 0%)  1.75fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     12f ( 0%)  1.76fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     13f ( 0%)  1.77fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     14f ( 0%)  1.78fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     15f ( 0%)  1.78fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     16f ( 0%)  1.79fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
^Cs:   0.0s     17f ( 0%)  1.80fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     18f ( 0%)  1.80fps Trem:   0min   0mb  A-V:0.000 [0:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:     -nan kbit/s  (-2147483648 B/s)  size: 0 bytes  0.000 secs  18 frames



Any help is greatly appreciated.

---

