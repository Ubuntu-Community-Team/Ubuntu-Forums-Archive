---
title: "Capturing video from a webcam?"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by godtvisken on 2007-05-20
What programs are available to capture video from a webcam? I've search around in the forums and haven't found any definitive answers yet.

Thanks

---

### Post by Cappy on 2007-05-20
I recommend [http://www.openwengo.org/](http://www.openwengo.org/)
The version on the website is reported to be better than the one in the repos.
amsn supports webcams also (a msn clone) but it never worked for me.

There are other programs, but those are the only two I know of that are cross platform.

---

### Post by godtvisken on 2007-05-20
Thank you for your response, but maybe I posed my question wrong. What I want to do is make videos with my webcamera, not use it to chat (well, I do, but I have already gotten that to work). So, I want to be able to record audio and video from the webcam, such as a "vcast" or so.

---

### Post by godtvisken on 2007-05-20
Bump

---

### Post by godtvisken on 2007-05-20
:?:

---

### Post by pauwl on 2007-05-22
I've tried the following:

**_Mencoder_**
but this needs to be run from the command line with:
```
mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi

```
My video camera over-exposes with this (I've a cheap logitech), and I can't find the settings to correct.

**_Xawtv_**
This has a GUI, and I could set the brightness properly, but failed to save to anything except split audio/video format.

**_Direct upload to Youtube_**
This worked OK, but grainy pictures as a result.

**_Kino_**
Doesn't recognise my webcam.

**_Camstreams_**
Recognises webcam, brightness can be set etc. etc., but is only for snapshots, or regular snapshots, no streaming.

**_gqcam_**
Also sees my webcam, but doesn't capture video, just snapshots.

So, not much for me I'm afraid. I will keep looking. Keep me posted if you find anything.

Pauwl

---

### Post by godtvisken on 2007-05-22
Regarding Mencoder: I can't seem to get that to work.. Errors. 

Though I'm having trouble remembering what I did to get it to work in Ekiga. I suppose I must modprobe something. 

```
jason@lycka:~$ mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 3100+ (Family: 15, Model: 28, Stepping: 0)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
This codecs.conf is too old and incompatible with this MPlayer release! at line 6
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: USB Video Class device
 Capabilites: capture 
 Device type: 1
 Supported sizes: 48x32 => 960x720
 Inputs: 1
ioctl get channel failed: Invalid argument
ioctl get mbuf failed: Invalid argument
Segmentation fault (core dumped)

```

```
jason@lycka:~$ mencoder tv:// -tv driver=**v4l2**:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 3100+ (Family: 15, Model: 28, Stepping: 0)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
This codecs.conf is too old and incompatible with this MPlayer release! at line 6
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: USB Video Class device
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Floating point exception (core dumped)

```

And regarding Kino, how does one check if the webcam is recognized? 

Thanks

---

### Post by godtvisken on 2007-05-25
Bump :neutral:

---

### Post by lamadredelsapo on 2007-06-03
Try MPEG4IP

---

### Post by BCtom on 2007-07-19
> **lamadredelsapo said:**
> Try MPEG4IP

Hi lamadredelsapo,

MPEG4IP looks like a really cool Webcam program, but..... I have being trying like crazy to install it. My last attempt was to convert the RPM, using "Alien" into a DEB file, but I keep getting are these types of errors...

>   Subprocess paste killed by signal (Broken Pipe)   

So I'm missing a pile of LIBs..... Which ones?

Do you know where I could get a pre-built DEB package of MPEG4IP since all I can fine are source files and RPM packages?

Streaming video from USB Web cams I thought were impossible using Linux: I'm glad to see this bridge finally crossed!   :)

---

### Post by sanicki on 2007-11-16
Bump

---

