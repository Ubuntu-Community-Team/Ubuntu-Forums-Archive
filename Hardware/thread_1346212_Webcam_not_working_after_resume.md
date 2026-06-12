---
title: "Webcam not working after resume"
date: 2009-12-04
forum: Hardware
---

### Post by chmac on 2009-12-04
I have a Lenovo X301 laptop. After hibernate and resume, the web cam stops working. I've had this issue since I got the laptop with the last 1 or 2 version of Ubuntu. Recently, the camera started working after resume. I assumed it was after a kernel upgrade. Then a few weeks later, the problem was back.

Originally, the /dev/video0 device would disappear after resume, there was an error on suspend about uvcvideo. This time, the /dev/video0 device exists, but the camera doesn't work. I get a generic error from luvcview.

```
$ luvcview
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: MJPG
Unable to set format: Input/output error
 Init v4L2 failed !! exit fatal
```

```
$ lsusb
Bus 001 Device 004: ID 17ef:4807 Lenovo
```

I've done a load of searching, but I haven't found anything related to suspend / resume errors. How can I debug this further?

---

### Post by chmac on 2009-12-04
Some more info if it's useful:

```
$ mplayer tv://
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (17ef:4807)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Input/output error
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.


Exiting... (End of file)
```

---

### Post by chmac on 2009-12-06
Another thing while I think about it, I've tried booting the two previous kernels, but no change. The webcam does not work with any of my currently installed kernels:
* 2.6.28-16-generic
* 2.6.28-15-generic
* 2.6.28-11-generic

I'm still running Ubuntu 9.04. I'll try upgrading to 9.10 at some point. Perhaps that will resolve the issue. I'm still optimistic about solving it on 9.04 because it was working until very recently.

---

### Post by gramound on 2010-09-05
Any updates on this issue?

I think I have the same problem on my Dell Vostro 1015 running Ubuntu 10.04 (2.6.32-24-generic). The luvcview output is identical, but my webcam is different:
```

$ lsusb -v
[...]
Bus 002 Device 002: ID 0408:20f5 Quanta Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x0408 Quanta Computer, Inc.
  idProduct          0x20f5 
  bcdDevice            3.03
  iManufacturer           2 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1

```

I noticed if I do a restart instead of shutdown, the webcam is completely gone after reboot (doesn't show up in lsusb).

Looks like the chip is stuck in sleep mode until full power down.

---

### Post by chmac on 2010-09-05
My webcam seems to work now after suspend. I didn't do anything in particular. It's a bug that seems to come and go over kernel versions. I'm assuming / hoping it'll eventually be figured out and I can forget about it... :-)

---

### Post by crquan on 2011-08-02
Me too, my Lenovo Thinkpad T410 with Ubuntu 10.10 also has this problem, webcam and /dev/video0 both disappear after resume, cheese or skype or gmail web video, any video program doesn't work;

but it didn't happen every time after resume;

```

cheng@cheng-ltop:~$ luvcview
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such file or directory
cheng@cheng-ltop:~$ uname -a
Linux cheng-ltop 2.6.35-30-generic-pae #54-Ubuntu SMP Tue Jun 7 20:28:33 UTC 2011 i686 GNU/Linux
cheng@cheng-ltop:~$ mplayer tv://
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: unable to open '/dev/video0': No such file or directory
v4l2: ioctl set mute failed: Bad file descriptor
v4l2: 0 frames successfully processed, 0 frames dropped.


Exiting... (End of file)


cheng@cheng-ltop:~$ lsusb
Bus 002 Device 003: ID 17ef:1003 Lenovo Integrated Smart Card Reader
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

I remember when it's working well, lsusb should have 4 or 5 usb dveices;

---

### Post by MarjaE on 2011-08-29
Same bug in 11.04.

---

