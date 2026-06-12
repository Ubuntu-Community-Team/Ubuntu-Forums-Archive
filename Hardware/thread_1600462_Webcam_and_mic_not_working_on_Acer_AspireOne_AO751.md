---
title: "Webcam and mic not working on Acer AspireOne AO751h"
date: 2010-10-19
forum: Hardware
---

### Post by pirx82 on 2010-10-19
Hi!

I'm running the Ubuntu Netbook Remix 10.04 LTS (32 bit) edition, and I've noticed, that the microphone and webcam don't work. I was trying to initiate an audio (and later audio/video) conversation via GoogleTalk, but my friend didn't hear or see me (at least I've heard him). Not only that - only a few second after initiating a video call, my browser (Firefox) crashed without any notice. It just closed itself.

I've tried to contact him again via Empathy, but it was the same. No audio, no video.

Any ideas please, what could be wrong, or what should I do?

Thanks!

---

### Post by pirx82 on 2010-10-19
Hi, guys. Any suggestions, please?

---

### Post by utilitytrack on 2010-10-19
Hello, try test your webcam:
```
$ mplayer tv:// -tv driver=v4l2:device=/dev/video0
```

And post here output.

---

### Post by pirx82 on 2010-10-19
Hi! Thank you for your reply.

It seems that the mplayer is not installed on my system. When I tried to install it from the Ubuntu Software Center, I got this message:

```
This error could be caused by required additional software packages  which are missing or not installable. Futhermore there could be a  conflict between software packages which are not allowed to be installed  at the same time.
```If I try it from the Terminal, I get this:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libavcodec52 (>= 4:0.6-1~) but it is not going to be installed or
                    libavcodec-extra-52 (>= 4:0.6-1~) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
           Depends: libavformat52 (>= 4:0.6-1~) but 4:0.5.1-1ubuntu1 is to be installed or
                    libavformat-extra-52 (>= 4:0.6-1~) but it is not going to be installed
E: Broken packages
```Is there an alternative to test the webcam? Thanks.

---

### Post by utilitytrack on 2010-10-19
Type it and follow instructions:
```
sudo aptitude install mplayer
```

---

### Post by pirx82 on 2010-10-19
Thank you. Your suggestion has worked! After the mplayer was installed and I've typed what you said, a pop-up window was started and it showed the image from my webcam! :)

The output from the terminal is this:

> MPlayer 1.0rc4-4.4.3 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: WebCam
 Capabilites:  video capture  streaming
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
v4l2: ioctl set mute failed: Invalid argument
libva: libva version 0.31.0-sds4
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/psb_drv_video.so
libva: va_openDriver() returns 0
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x8b202e0]BICUBIC scaler, from yuyv422 to nv12 using MMX2
VO: [vaapi] 640x480 => 640x480 Planar NV12 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...


Also, I've installed the Audacity recording software and it seems that the built-in microphone is working fine there. However, I am not sure, why it is not working under Sound Preferences -> Input.

Any insights on this?

Thanks again, your help is much appreciated.

---

### Post by utilitytrack on 2010-10-20
Please mark this thread as solved.

---

### Post by pirx82 on 2010-10-20
It's done. :)

So this installed the needed drivers? All I saw was that libavcodec52 was being upgraded from some kind of beta to a stable release.

Thanks.

---

