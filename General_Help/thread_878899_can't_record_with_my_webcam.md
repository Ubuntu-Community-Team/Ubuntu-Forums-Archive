---
title: "can't record with my webcam"
date: 2008-08-03
forum: General Help
---

### Post by kekalizarazo on 2008-08-03
Hi I have a dell 1420 with integrated webcam with ubuntu hardy. The webcam works great with ekiga and with amsn. 
But i can't record clips with it.
I've tried with Mplyer (mencoder) and this is what I get:


yotas@dell-laptop:~$ mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU T5450 @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9 data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l
name: Video 4 Linux input
author: Alex Beregszaszi
comment: under development
================================================== ===============
WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
As the V4L1 compatibility layer is broken, this may not work.
If you encounter any problems, use driver=v4l2 instead.
Bugreports on driver=v4l with v4l2 drivers will be ignored.
================================================== ===============
Selected device: Laptop Integrated Webcam
Capabilites: capture
Device type: 1
Supported sizes: 48x32 => 1600x1200
Inputs: 1
ioctl get channel failed: Invalid argument
Unable to open '/dev/dsp1': No such file or directory
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.


I change the v4l to v4l2 and fix the the audio to /dev/dsp
yotas@dell-laptop:~$ mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU T5450 @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9 data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
name: Video 4 Linux 2 input
author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
comment: first try, more to come
v4l2: ioctl get standard failed: Invalid argument
Selected device: Laptop Integrated Webcam
Capabilites: video capture streaming
supported norms:
inputs: 0 = Camera 1;
Current input: 0
Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
floating coma exception


with Freej I get this error
engine running at 24 FPS
v4l: size 320x240 not supported res: -1
create_layer : V4L open failed[*] Closing video4linux grabber layer
closing video4linux device 9
can't create a layer with /dev/video0
can't open captura.avi to create a Layer: No such file or directory

I've also tried with cheese, and when I record I can't see the video in the space below. When I close the program the video in the folder disappears, but if I play it, it goes too fats and i get no audio. 
I tried with vlc with this instructions [http://ubuntuforums.org/showthread.php?t=143732](http://ubuntuforums.org/showthread.php?t=143732)
I record the audio but not the video, but when I begin to record my webcam's light is on.

I'm tired of trying and trying, and I've spent too many hour with this issue.
Can anyone help me please?

---

### Post by rEbyTer on 2008-08-03
Try with cheese.
```

$ sudo apt-get install cheese
```

---

### Post by kekalizarazo on 2008-08-04
> **kekalizarazo said:**
> 

[COLOR="Yellow"]I've also tried with cheese, and when I record I can't see the video in the space below. When I close the program the video in the folder disappears, but if I play it, it goes too fats and i get no audio. 
?
 I said that I've already tried with cheese

---

### Post by josvanr on 2008-12-06
my advice: buy a digital video cam

aaaargh

---

