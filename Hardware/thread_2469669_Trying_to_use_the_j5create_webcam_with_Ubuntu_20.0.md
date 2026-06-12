---
title: "Trying to use the j5create webcam with Ubuntu 20.04"
date: 2021-12-06
forum: Hardware
---

### Post by willsattnz on 2021-12-06
I'm trying to get the [j5create JVCU100]("https://en.j5create.com/products/jvcu100") webcam to work with my Ubuntu desktop. So far I can get an image but it is highly unstable &#128580;&#65039;

It uses UVC, which means it *should* work without installing a specific driver, however when I first plugged it in and opened cheese, no device was found. Ubuntu did however detect the built in microphone.

I started working down [this]("https://help.ubuntu.com/community/Webcam") list of software that should display a webcam, before finally mplayer worked, using the command ```
mplayer tv:// -tv driver=v4l2:width=1920:height=1080:device=/dev/video0
```

I didn't have mplayer installed, so I wonder if installing brought in some dependencies the camera needed? After running mplayer, the camera worked with both Zoom (1080p resolution) and Cheese, although cheese couldn't uses the native 1080p resolution and only displayed a low-res, incorrect aspect ratio version.

After restarting I released just how unstable this setup was. First it seems that I need to open the camera stream in mplayer before other applications will work. Second I need to hotplug the camera for mplayer to recognise it. Third, this doesn't always work, requiring me to unplug and re-plug in the camera before trying again. Fourth, sometimes it works at first, but if I close mplayer and try to open it again it gets stuck and I have have to end to process, or mplayer gets an EOF signal and quits.

Unfortunately I cannot tell what the camera will do after plugging it in without trying, sometimes it works and sometimes it doesn't. I realise this makes it extra tricky to diagnose the problem as it is not 100% reproducible. 

If anyone else uses a similar webcam or has experience fixing unstable webcams I'll all ears

Here are some outputs that might help:

```
$ lsusb
<mouse and keyboard etc>
Bus 003 Device 027: ID 0711:3108 Magic Control Technology Corp. j5 WebCam JVCU100
```

```
$ v4l2-ctl --list-devices
j5 WebCam JVCU100: j5 WebCam JV (usb-0000:00:14.0-10):
    /dev/video0
    /dev/video1
```

```
$ v4l2-ctl --list-format
sioctl: VIDIOC_ENUM_FMT
    Type: Video Capture


    [0]: 'MJPG' (Motion-JPEG, compressed)
    [1]: 'H264' (H.264, compressed)
    [2]: 'YUYV' (YUYV 4:2:2)
```

mplayer when it opens normally:
```
$ mplayer tv:// -tv driver=v4l2:width=1920:height=1080:device=/dev/video0MPlayer 1.3.0 (Debian), built with gcc-9 (C) 2000-2016 MPlayer Team
do_connect: could not connect to socket
connect: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: j5 WebCam JVCU100: j5 WebCam JV
 Capabilities:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Input/output error
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Inappropriate ioctl for device
Error: Cannot set norm!
v4l2: ioctl set width failed: Input/output error
v4l2: ioctl set height failed: Input/output error
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl set Saturation 0 failed: Broken pipe
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 58.54.100 (external)
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
Audio: no sound
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 1920x1080 => 1920x1080 Planar YV12 
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 1920x1080 => 1920x1080 Planar YV12 
V:   0.0 12060/12060 ??% ??% ??,?% 0 0 
v4l2: ioctl set mute failed: Invalid argument
v4l2: 12062 frames successfully processed, 1 frames dropped.


Exiting... (Quit)
```

mplayer when it tries to open the camera, gets suck and I end the process.
```
$ mplayer tv:// -tv driver=v4l2:width=1920:height=1080:device=/dev/video0MPlayer 1.3.0 (Debian), built with gcc-9 (C) 2000-2016 MPlayer Team
do_connect: could not connect to socket
connect: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: j5 WebCam JVCU100: j5 WebCam JV
 Capabilities:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Input/output error
v4l2: ioctl set format failed: Input/output error
v4l2: ioctl set format failed: Input/output error
v4l2: ioctl set format failed: Input/output error




MPlayer interrupted by signal 2 in module: demux_open
v4l2: ioctl set format failed: Input/output error
```

mplayer when it gets and EOF signal:
```
mplayer tv:// -tv driver=v4l2:width=1920:height=1080:device=/dev/video0MPlayer 1.3.0 (Debian), built with gcc-9 (C) 2000-2016 MPlayer Team
do_connect: could not connect to socket
connect: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: unable to open '/dev/video0': Permission denied
v4l2: ioctl set mute failed: Bad file descriptor
v4l2: 0 frames successfully processed, 0 frames dropped.




Exiting... (End of file)
```

I see the EOF problem is caused by not being able to access /dev/video0, but I don't understand why mplayer would have the permission denied for accessing that.

---

