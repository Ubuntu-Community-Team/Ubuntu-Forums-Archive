---
title: "[HELP] Radeon HD 5450 on Ubuntu 20.04 drivers needed"
date: 2020-12-18
forum: Hardware
---

### Post by marwalmw on 2020-12-18
[COLOR=#000000][FONT=&amp]Hello, I have Radeon HD 5450 on Ubuntu 20.04 and using standard drivers installed by Ubuntu during the system installation. I noticed that while watching for example Netflix or YouTube, videos are not smooth and fluent as it used to be while using Windows on this machine. I can't find drivers for my Radeon HD 5450 video card for Ubuntu 20.04, can you help me, which driver should I choose or what I can do to fix it? [/FONT][/COLOR]

---

### Post by QIII on 2020-12-18
Unfortunately, you have no options.  The Catalyst driver that one used to be able to install is no longer maintained and will not work with modern versions of Linux.

When Ubuntu (and most other Linux distros) is installed, the installer detects the GPU hardware.  If the AMD hardware is supported by the open source AMDGPU module, that module is activated.  If not, the open source radeon module is activated.

There are no options beyond those.

You will see people here still recommending some PPAs with supposedly better drivers.  Don't be fooled.  The correct and best "drivers" are kernel modules and are updated via kernel updates.

At best anything offered by those PPAs will cause the failure of any updates through the normal Ubuntu process.  At worst, they will render your machine inoperative.

---

### Post by mastablasta on 2020-12-21
what kernel are you using? please post result of 

uname -a

AMD drivers in kernel should perform well for games and videos. i too have an older chip and have not noticed any issues.¸i also have new chip and there are no issue there as well. 

if you are using ubuntu you can try switching to xorg instead of wayland and see if that will improve things.

xorg has a bunch of switches, but you would need ot know what they do: [https://www.x.org/releases/current/doc/man/man4/radeon.4.xhtml](https://www.x.org/releases/current/doc/man/man4/radeon.4.xhtml)

here are the features avaialble in xorg: [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

---

### Post by Yellow Pasque on 2020-12-23
The RadeonHD 5450 is simply too old to accelerate the formats Youtube uses nowadays, like VP9 and AV1. (I'm not sure what Netflix uses). Your best bet for Youtube is probably the "h264ify" extension. At least the 5450 supports H.264 decode acceleration.

You can see vainfo for what formats your GPU can accelerate in web browsers:
```
vainfo
```

---

