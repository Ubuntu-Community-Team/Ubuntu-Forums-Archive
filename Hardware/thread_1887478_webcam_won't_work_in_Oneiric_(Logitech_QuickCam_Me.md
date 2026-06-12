---
title: "webcam won't work in Oneiric (Logitech QuickCam Messenger)"
date: 2011-11-27
forum: Hardware
---

### Post by thoughts on 2011-11-27
Hello,

I have a Logitech QuickCam Messenger USB webcam (device ID 046d:08f0), which worked properly and automatically under previous versions of Ubuntu.  I just had to plug it in, and then webcam apps could see it automatically.

But then a month ago, I did the "upgrade" to Ubuntu 11.10.  I say "upgrade" in quotes because this upgrade has been an unmitigated disaster, with tons of stuff breaking, and what hasn't broken is changed in ways that make it worse than before.  I've been running Ubuntu upgrades on this same system (and other systems) for years without too much trouble, but 11.10 has been a nightmare.

I've managed to fix some of the problems, but the webcam I can't figure out.  It seems like perhaps the newer version of v4l doesn't support my webcam anymore, but that doesn't really make sense; why would they *remove* support for devices?

When I plug in the webcam, I do get a /dev/video0 device; but webcam apps report errors when I try to access it, for example:

```

$ cheese
[...]
libv4l2: error turning on stream: Input/output error
** (cheese:17433): WARNING **: Error starting streaming on device '/dev/video0'.
** (cheese:17433): WARNING **: Could not negotiate format

$ streamer -c /dev/video0 -o image.jpeg
files / video: JPEG (JFIF) / audio: none
libv4l2: error turning on stream: Input/output error
ioctl: VIDIOC_STREAMON(int=1): Input/output error
v4l2: oops: select timeout
v4l2: oops: select timeout
v4l2: oops: select timeout
[...]

```

Any ideas on how to make this webcam work in Oneiric?  I've done a ton of web searching and trying different things, to no avail.  The most promising lead seemed to be this QuickCam Messenger driver:

	[http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)

But trying to build it results in an error (quickcam.h:95:28: fatal error: linux/autoconf.h: No such file or directory), which appears to be due to the fact that the driver is really old (~4 years) and is looking for files in the kernel that have since been moved to different locations in newer kernels.

Thanks for any help you can offer.

--
Anthony DiSante

---

### Post by Carterclan on 2011-11-27
My Webcam is a logitech quickcam with an id (046d:08da), it is working fine except in Skype (which is nothing new). I'm also running 11.10.

It sounds to me as though your upgrade didn't go as well as it should have done. Might be worth considering backing-up and doing a fresh install

---

### Post by BC59 on 2011-11-27
> **thoughts said:**
> Hello,

I have a Logitech QuickCam Messenger USB webcam (device ID 046d:08f0), which worked properly and automatically under previous versions of Ubuntu.  I just had to plug it in, and then webcam apps could see it automatically.

But then a month ago, I did the "upgrade" to Ubuntu 11.10.  I say "upgrade" in quotes because this upgrade has been an unmitigated disaster, with tons of stuff breaking, and what hasn't broken is changed in ways that make it worse than before.  I've been running Ubuntu upgrades on this same system (and other systems) for years without too much trouble, but 11.10 has been a nightmare.

I've managed to fix some of the problems, but the webcam I can't figure out.  It seems like perhaps the newer version of v4l doesn't support my webcam anymore, but that doesn't really make sense; why would they *remove* support for devices?

When I plug in the webcam, I do get a /dev/video0 device; but webcam apps report errors when I try to access it, for example:

```

$ cheese
[...]
libv4l2: error turning on stream: Input/output error
** (cheese:17433): WARNING **: Error starting streaming on device '/dev/video0'.
** (cheese:17433): WARNING **: Could not negotiate format

$ streamer -c /dev/video0 -o image.jpeg
files / video: JPEG (JFIF) / audio: none
libv4l2: error turning on stream: Input/output error
ioctl: VIDIOC_STREAMON(int=1): Input/output error
v4l2: oops: select timeout
v4l2: oops: select timeout
v4l2: oops: select timeout
[...]

```

Any ideas on how to make this webcam work in Oneiric?  I've done a ton of web searching and trying different things, to no avail.  The most promising lead seemed to be this QuickCam Messenger driver:

	[http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)

But trying to build it results in an error (quickcam.h:95:28: fatal error: linux/autoconf.h: No such file or directory), which appears to be due to the fact that the driver is really old (~4 years) and is looking for files in the kernel that have since been moved to different locations in newer kernels.

Thanks for any help you can offer.

--
Anthony DiSante

Well the most comprehensive document about webcams is here: 

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

and I think you tried everything it comments.

So I tend to support Carterclan's suggestion to do a fresh install.

---

### Post by thoughts on 2011-11-29
Well, I really don't have the time to go through the hassle of a reinstall at this point; and realistically, if I'm going to do a clean install, then it's not going to be Ubuntu -- it's probably going to be Linux Mint, or possibly Fedora.

In the meantime though, I found another solution: this four-dollar webcam from Amazon:

[http://www.amazon.com/Webcam-Camera-Vision-Meeting-compatible/dp/B0015TJNEY/](http://www.amazon.com/Webcam-Camera-Vision-Meeting-compatible/dp/B0015TJNEY/)

I got it, plugged it in, and it's recognized automatically, and works with no hassle in apps like cheese and streamer, just like my Logitech webcam used to in previous versions of Ubuntu.  And it's twice the resolution of my old webcam too.  (Its device ID is 1e4e:0102, for anyone interested.)

Now my only concern is, how in the heck is this thing just four bucks??  My guess is that it's loaded with some kind of spyware/virus and is secretly sending all my keystrokes/data to a server somewhere in China... hopefully it's Windows-based spyware.

--
Anthony DiSante

---

