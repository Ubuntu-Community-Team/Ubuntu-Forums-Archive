---
title: "How to turn off webcam's LED"
date: 2011-03-09
forum: Hardware
---

### Post by emab on 2011-03-09
Hi,
I want to record video using my web cam,
but when I use cheese or ffmpeg, the LED turns on.

do you know a way to record video with web cam and avoid the LED of being turned on?

model of web cam is:
       OmniVision Technologies, Inc. OV2640 Webcam
and I'm using ubuntu

thank you

---

### Post by Grenage on 2011-03-09
> **emab said:**
> Hi,
I want to record video using my web cam,
but when I use cheese or ffmpeg, the LED turns on.

do you know a way to record video with web cam and avoid the LED of being turned on?

than you

Sneaking in some 'home movies'? ;)

Seriously though, would it not be easiest to tape over it, or physically disconnect it?

---

### Post by emab on 2011-03-09
> **Grenage said:**
> Sneaking in some 'home movies'? ;)

Seriously though, would it not be easiest to tape over it, or physically disconnect it?

I want to test software capabilities in ubuntu.

---

### Post by zenwalker on 2011-03-09
Seems like the resource acquired by your driver for that cam isnt releasing when you close the application. There could be a bug in the driver as well. See if your vendor does provide some good drivers or try to contact its maintainer. 

Also do let us know how your using ffmpeg or cheese. Because, unless you pass parameter to ffmpeg or use an option in cheese to use webcam, they dont ping the device. I use those apps too.

---

### Post by emab on 2011-03-09
> **zenwalker said:**
> Seems like the resource acquired by your driver for that cam isnt releasing when you close the application. There could be a bug in the driver as well. See if your vendor does provide some good drivers or try to contact its maintainer. 

Also do let us know how your using ffmpeg or cheese. Because, unless you pass parameter to ffmpeg or use an option in cheese to use webcam, they dont ping the device. I use those apps too.

for recording I use:
```
ffmpeg -f oss -i /dev/dsp -f video4linux2 -s 320x240 -i /dev/video0 out.mpg
```

---

