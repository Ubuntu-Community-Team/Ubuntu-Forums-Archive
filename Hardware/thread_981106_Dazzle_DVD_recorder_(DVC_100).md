---
title: "Dazzle DVD recorder (DVC 100)"
date: 2008-11-13
forum: Hardware
---

### Post by Coollie on 2008-11-13
Hello Ubuntu community,

I would like some help on configuring my ubuntu. I have a Dazzle DVD 100 recorder which I bought to use with my media center so I could capture some old movies I still had on tapes. I don't want to use XP or Vista. I've been using Ubuntu for some time now and I just can't get enough of ubuntu.

So here's my problem; after doing a some research on the internet I found some linux topics on the DVC 100 (that's how it's called). Finally I found some info on how to configure my Ubuntu Hardy to work with the DVC 100. Some of this info is based on kernels that have long been replaced with newer kernels where the DVC 100 is being supported. Still after reading a lot of forums I managed to compile a driver with my current kernel and got it to work. Downside is that I have no sound when recording.

Below you'll find the links (and thus method) I used to get it to work and those who didn't work. Also I will post my dmesg output and other info. I would appreciate if someone could help me to get the DVC 100 working correctly. My current kernel version is: 2.6.24-21-generic.

Thnx in advance.

1. [Working]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.equinoxefr.org%2Fpost%2F2008%2F09%2F05%2Fdazzle-dvc-100-sous-ubuntu-804%2F&hl=nl&ie=UTF-8&sl=fr&tl=en") method.Translated thru Google translator.

2. [Unsuccessful]("http://74.125.93.104/translate_c?hl=en&langpair=fr|en&u=http://lea-linux.org/cached/index/Num%25C3%25A9riser_vos_anciennes_cassettes_VHS_sous_Linux.html&usg=ALkJrhiAf-H7WGVVt77Hj98CUIVcR3gIBw") method. Also translated thru Google translator.

3. Some more [info]("http://www.linuxquestions.org/questions/linux-hardware-18/dazzle-dvd-recorder-497596/")

---

### Post by Silvernail on 2008-11-13
Below is the tail of my 'dmesg'.

I did notice that while I was compiling an error message came up several times about '_memcpy' if thats any help.

Got any suggestions where I go from here? What other information can I provide?

131.471048] usb 4-1: new high speed USB device using ehci_hcd and address 4
[  131.609212] usb 4-1: configuration #1 chosen from 1 choice
[  131.923731] usbcore: registered new interface driver snd-usb-audio
[  131.972256] em28xx: disagrees about version of symbol v4l_compat_ioctl32
[  131.972275] em28xx: Unknown symbol v4l_compat_ioctl32
[  131.981033] em28xx: disagrees about version of symbol v4l_compat_ioctl32
[  131.981056] em28xx: Unknown symbol v4l_compat_ioctl32
[  131.994773] em28xx: disagrees about version of symbol v4l_compat_ioctl32
[  131.994797] em28xx: Unknown symbol v4l_compat_ioctl32
dave@Dafydd:~$ 

And this is the head of 'dmesg'
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic

---

### Post by Coollie on 2008-11-14
Hi Silvernail, no i have no idea. Maybe you can reboot your system? I can remember that I had similar error messages. After a reboot and recompiling the driver, all was gone.
Thanks for the help. GreetZ!

---

### Post by Coollie on 2008-11-15
Anybody any ideas how I could solve this problem?

Greetz

Coollie

---

### Post by Coollie on 2008-11-16
Okay Guys, got me some new information. Every time I try to record from de DV cam the audio frames get dropped after 30 seconds by mencoder.
```

root@xxx:/# mencoder tv://-tv\driver=v4l2: width=720: height=576: norm=PAL-BG: audiorate=44100: immediatemode=0: forceaudio: adevice=/dev/dsp1 -o test.avi -ovc lavc -lavcopts vcodec=mjpeg: aspect=4/3-aspect 4:3\ -noautoexpand OAC-pcm-endpos 1:30:00
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1500MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option stream url: This URL doesn't have a port part.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Pinnacle Dazzle DVC 90/DVC 100
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = NTSC-443; 5 = PAL; 6 = PAL-BG; 7 = PAL-H; 8 = PAL-I; 9 = PAL-DK; 10 = PAL-M; 11 = PAL-N; 12 = PAL-Nc; 13 = PAL-60; 14 = SECAM; 15 = SECAM-B; 16 = SECAM-G; 17 = SECAM-H; 18 = SECAM-DK; 19 = SECAM-L; 20 = SECAM-Lc;
 inputs: 0 = Composite1; 1 = S-Video;
 Current input: 0
 Current format: YUYV
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
[V] filefmt:9  fourcc:0x32595559  size:640x480  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x880f730]SwScaler: BICUBIC scaler, from yuyv422 to yuv420p using MMX2
[swscaler @ 0x880f730]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x880f730]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x880f730]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x880f730]SwScaler: 640x480 -> 640x480
videocodec: libavcodec (640x480 fourcc=47504a4d [MJPG])
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   1.5s     38f ( 0%) 24.08fps Trem:   0min   0mb  A-V:0.000 [9566:0]
1 duplicate frame(s)!
Pos:  34.1s    851f ( 0%) 24.95fps Trem:   0min   0mb  A-V:0.000 [9565:0]
too bad - dropping audio frame !
Pos:  34.1s    852f ( 0%) 24.93fps Trem:   0min   0mb  A-V:0.000 [9566:0]
too bad - dropping audio frame !
Pos:  34.2s    855f ( 0%) 24.95fps Trem:   0min   0mb  A-V:0.000 [9566:0]
too bad - dropping audio frame !
Pos:  34.3s    857f ( 0%) 24.94fps Trem:   0min   0mb  A-V:0.000 [9567:0]
too bad - dropping audio frame !
Pos:  34.4s    860f ( 0%) 24.95fps Trem:   0min   0mb  A-V:0.000 [9569:0]
too bad - dropping audio frame !

--------------------- Second Try --------------------- 

root@xxx:/# mencoder tv://-tv\driver=v4l2: width=720: height=576: norm=PAL-BG: audiorate=44100: immediatemode=0: forceaudio: adevice=/dev/dsp1 -o test1.avi -ovc lavc -lavcopts vcodec=mjpeg: aspect=4/3-aspect 4:3\ -noautoexpand OAC-pcm-endpos 1:30:00
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1500MHz (Family: 6, Model: 9, Stepping: 5)

CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option stream url: This URL doesn't have a port part.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Pinnacle Dazzle DVC 90/DVC 100
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = NTSC-443; 5 = PAL; 6 = PAL-BG; 7 = PAL-H; 8 = PAL-I; 9 = PAL-DK; 10 = PAL-M; 11 = PAL-N; 12 = PAL-Nc; 13 = PAL-60; 14 = SECAM; 15 = SECAM-B; 16 = SECAM-G; 17 = SECAM-H; 18 = SECAM-DK; 19 = SECAM-L; 20 = SECAM-Lc;
 inputs: 0 = Composite1; 1 = S-Video;
 Current input: 0
 Current format: YUYV
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
[V] filefmt:9  fourcc:0x32595559  size:640x480  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x880f730]SwScaler: BICUBIC scaler, from yuyv422 to yuv420p using MMX2
[swscaler @ 0x880f730]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x880f730]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x880f730]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x880f730]SwScaler: 640x480 -> 640x480
videocodec: libavcodec (640x480 fourcc=47504a4d [MJPG])
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.5s     13f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Pos:  34.0s    850f ( 0%) 24.95fps Trem:   0min   0mb  A-V:0.000 [9707:0]
too bad - dropping audio frame !
Pos:  34.1s    852f ( 0%) 24.94fps Trem:   0min   0mb  A-V:0.000 [9706:0]
too bad - dropping audio frame !
Pos:  34.2s    855f ( 0%) 24.95fps Trem:   0min   0mb  A-V:0.000 [9706:0]
too bad - dropping audio frame !
Pos:  34.3s    857f ( 0%) 24.95fps Trem:   0min   0mb  A-V:0.000 [9706:0]
too bad - dropping audio frame !
Pos:  34.4s    860f ( 0%) 24.94fps Trem:   0min   0mb  A-V:0.000 [9706:0]
too bad - dropping audio frame !
Pos:  34.5s    862f ( 0%) 24.94fps Trem:   0min   0mb  A-V:0.000 [9706:0]
too bad - dropping audio frame !

```

Have anybody seen this before?

Greetz!

---

