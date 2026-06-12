---
title: "Lenovo ideapad U110"
date: 2009-04-14
forum: Hardware
---

### Post by dpvvdt on 2009-04-14
Hello! Anybody can help solve problem with mic and camera in this laptop (ubuntu 9.04)?

[http://www.linlap.com/wiki/lenovo+ideapad+u110](http://www.linlap.com/wiki/lenovo+ideapad+u110)

---

### Post by dpvvdt on 2009-04-14
No one with u110?

---

### Post by coldmack on 2009-05-12
I would like to see a bump as I am thinking about purchasing this device in the future.

---

### Post by linux-dude on 2010-06-29
I have the same problem with Ubuntu 10.04. does anyone have a lenovo u110 with working Webcam and Mic?

---

### Post by aloysiuscarl on 2010-06-30
The U110 is thinner and has a faster processor 1.6GHz L7500 versus 1.2GHz SL7100 but no optical drive and a slower, smaller HDD. Hard to say which is a better value; depends on your needs.The thermal design of the U110 is surprisingly good. Keyboard and palmrest surfaces remained in the double-digit temperature range and the bottom of the notebook barely crossed into triple digits after stressing the system by running benchmarks.

---

### Post by silveraden on 2010-06-30
> **dpvvdt said:**
> Hello! Anybody can help solve problem with mic and camera in this laptop (ubuntu 9.04)?

[http://www.linlap.com/wiki/lenovo+ideapad+u110](http://www.linlap.com/wiki/lenovo+ideapad+u110)

Too bad, I already sold mine.. I can't test.

---

### Post by langmarp on 2010-07-09
same problem - no solution...

---

### Post by willPower on 2010-09-01
> **linux-dude said:**
> I have the same problem with Ubuntu 10.04. does anyone have a lenovo u110 with working Webcam and Mic?

Both of these work on mine. The camera works great, but I have to use an external microphone, as I haven't figured out how to get the built-in one to work.

The camera uses the uvcvideo module, and it must be loaded with a parameter (quirks=2 or something like that), otherwise the video won't work.

---

### Post by langmarp on 2010-09-06
> **willPower said:**
>  camera uses the uvcvideo module, and it must be loaded with a parameter (quirks=2 or something like that) 

could you please describe this solution in its detailed?
thank you!

---

### Post by willPower on 2010-09-08
> **langmarp said:**
> could you please describe this solution in its detailed?
thank you!

Try this:

Check to see if the uvcvideo kernel module is already loaded:
```

$ lsmod | grep uvc
uvcvideo          56990   0
videodev          34361   1 uvcvideo
v4l1_compat       13251   2 uvcvideo,videodev

```

If it is, then rmmod it:
```

$ sudo rmmod uvcvideo

```

Then, modprobe it using the quirks=2 parameter:
```

$ sudo modprobe uvcvideo quirks=2

```

Now check to see that your camera is working:
```

mplayer -fps 15 tv://

```

Some of this was adapted from [http://bitsandchaos.wordpress.com/](http://bitsandchaos.wordpress.com/).

---

### Post by langmarp on 2010-10-12
any success with 10.10?

---

### Post by langmarp on 2010-10-17
@willPower
I have tried your solution under 10.10, but nothing has happened.
Could you give me some further information?
Thanks

berkovics@berkovics-laptop:~$ lsmod | grep uvc
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
berkovics@berkovics-laptop:~$ sudo rmmod uvcvideo
[sudo] password for berkovics: 
berkovics@berkovics-laptop:~$ sudo modprobe uvcvideo quirks=2
berkovics@berkovics-laptop:~$ mplayer -fps 15 tv://
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
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: USB2.0 UVC PC Camera
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Input/output error
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.


Exiting... (End of file)
berkovics@berkovics-laptop:~$

---

