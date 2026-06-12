---
title: "Configuration of nouveau video driver"
date: 2015-03-14
forum: Hardware
---

### Post by mickee384 on 2015-03-14
Hi!

Try as I might I cannot find a way to configure the driver. I see only screen resolution. I have some choppy video and wanted to tweak the video performance. Is there a GUI available fort the driver?

---

### Post by Vladlenin5000 on 2015-03-14
There are no tweaks, let alone a GUI... It is what it is. If you need better performance install proprietary drivers instead.

---

### Post by mickee384 on 2015-03-24
I used to have an Nvidia driver for my Geforce 9300M. This time, after installing an Nvidia driver, the computer froze completely after about a minute. I was also unable to get in and load the noveau one back in as it would freeze up before I had an opportunity. I ended up having to reinstall ubuntu. How do I know which Nvidia driver to use. I searched the forums and internet, but could not come up with a solution.  Here is more info on my card.  NVIDIA GeForce 9300 M GS HD graphics module with 256MB dedicated video memory

do you require info about the computer as well? I am eager to learn, but I don't want to have to reinstall again.

---

### Post by Yellow Pasque on 2015-03-24
If you want to go the proprietary blob route, then I'd recommend using this PPA: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
The nvidia 340.xx branch is the last one to support your GPU.

As for the present open-source driver, you can video acceleration working, but it requires some hacking:
```
mkdir /tmp/nouveau
cd /tmp/nouveau
wget https://raw.github.com/imirkin/re-vp2/master/extract_firmware.py
wget http://us.download.nvidia.com/XFree86/Linux-x86/325.15/NVIDIA-Linux-x86-325.15.run
sh NVIDIA-Linux-x86-325.15.run --extract-only
python2 extract_firmware.py
sudo mkdir /lib/firmware/nouveau
sudo cp -d nv* vuc-* /lib/firmware/nouveau/
sudo apt-get install mesa-vdpau-drivers vdpauinfo
```

Then, you can run vdpauinfo command to verify and it should look something like this:
```
$ vdpauinfo

display: :0.0   screen: 0
API version: 1
Information string: G3DVL VDPAU Driver Shared Library version 1.0

Video surface:

name   width height types
-------------------------------------------
420     8192  8192  NV12 YV12 
422     8192  8192  UYVY YUYV 
444     8192  8192  Y8U8V8A8 V8U8Y8A8 

Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                           0 16384  2048  2048
MPEG2_SIMPLE                    3 16384  2048  2048
MPEG2_MAIN                      3 16384  2048  2048
H264_BASELINE                  41 16384  2048  2048
H264_MAIN                      41 16384  2048  2048
H264_HIGH                      41 16384  2048  2048
VC1_SIMPLE                      1 16384  2048  2048
VC1_MAIN                        2 16384  2048  2048
VC1_ADVANCED                    4 16384  2048  2048
```

---

### Post by mickee384 on 2015-03-24
Thanks so much for the 2 alternatives. I appreciate it.

---

### Post by mickee384 on 2015-03-24
Ok, so. I added the Nvidia ppa mamarley/nvidia. I found a 340 driver in Software & Updates. I applied the new driver and rebooted. I knew there would be an issue as Plymouth resolution was wacked. I logged on and launched teh Software & Updates agin to change back to nouveau. The same issue I had before as the pc seems to freeze. The keyboard was frozen, but I heard hard disk activity. The mosue was still active, so I think the desktop (X?, Unity? lightdm? Sorry, I am a little ignorant with things ubuntu, but what I learn sticks with me) was frozen. I waited this time and after 5 minutes I did a hard power off. It booted back up with nouveau. So the weird thing I have is that just the desktop and keyboards froze with the Nvidia driver. 

So am back on noveau w/o having to reinstall. (Yay!). As far as an explantion goes, I have none. Anyone know why these 2 things froze?

---

### Post by mickee384 on 2015-03-24
I tried all drivers in "Software' additional - all but nouveau freeze still. At least I was able to revert back. These are the ones in my additional drivers section: 173.14.39 (This I think was one I used in 13.10), 331.13, 304.125. I also tried the 340 driver as suggested. I will try the  .run 

any other ideas? :-)

---

### Post by mickee384 on 2015-03-25
Ok, so I did a chmod +x on that .run. Tried riunning said need to exit from X. Did a CTRL + Alt F1. Then ran from there. Same message so I did /etc/init.d/lightdm stop. Got a strange screen and it said I was running in low graphics mode. The keyboard (usb) wouldn't work so couldn't do a sudo restart so did a hard power down. So and I am back in, still with the noveau driver. Not sure where to go next.

---

### Post by Yellow Pasque on 2015-03-25
Maybe you should just stick to the nouveau driver. I have a very similar GPU based on the same G98 core and I've switched to nouveau. It works very well on older Nvidia cards like ours once VDPAU is setup with the commands I posted above. It even has full support for OpenGL 3.3 assuming you are using new enough mesa.
```
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NV98
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.4.2
OpenGL core profile shading language version string: 3.30
```

---

### Post by mickee384 on 2015-03-25
Thanks, Temüjin. I will try that when I get home.

---

### Post by mickee384 on 2015-03-25
ok so I followed that. Here is my result of vdpauinfo:
```
mickee@mickeymouse:~&#10219; vdpauinfo
display: :0   screen: 0
API version: 1
Information string: G3DVL VDPAU Driver Shared Library version 1.0

Video surface:

name   width height types
-------------------------------------------
420     8192  8192  NV12 YV12 
422     8192  8192  UYVY YUYV 
444     8192  8192  Y8U8V8A8 V8U8Y8A8 

Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                           0 16384  2048  2048
MPEG2_SIMPLE                    3 16384  2048  2048
MPEG2_MAIN                      3 16384  2048  2048
H264_BASELINE                  41 16384  2048  2048
H264_MAIN                      41 16384  2048  2048
H264_HIGH                      41 16384  2048  2048
VC1_SIMPLE                      1 16384  2048  2048
VC1_MAIN                        2 16384  2048  2048
VC1_ADVANCED                    4 16384  2048  2048
MPEG4_PART2_SP                 --- not supported ---
MPEG4_PART2_ASP                --- not supported ---
DIVX4_QMOBILE                  --- not supported ---
DIVX4_MOBILE                   --- not supported ---
DIVX4_HOME_THEATER             --- not supported ---
DIVX4_HD_1080P                 --- not supported ---
DIVX5_QMOBILE                  --- not supported ---
DIVX5_MOBILE                   --- not supported ---
DIVX5_HOME_THEATER             --- not supported ---
DIVX5_HD_1080P                 --- not supported ---
H264_CONSTRAINED_BASELINE      --- not supported ---
H264_EXTENDED                  --- not supported ---
H264_PROGRESSIVE_HIGH          --- not supported ---
H264_CONSTRAINED_HIGH          --- not supported ---
H264_HIGH_444_PREDICTIVE       --- not supported ---

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8          8192  8192    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R8G8B8A8          8192  8192    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R10G10B10A2       8192  8192    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
B10G10R10A2       8192  8192    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8          8192  8192
R8G8B8A8          8192  8192
R10G10B10A2       8192  8192
B10G10R10A2       8192  8192
A8                8192  8192

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     -
INVERSE_TELECINE                 -
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         -
HIGH QUALITY SCALING - L1        -
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y        48     2048
VIDEO_SURFACE_HEIGHT             y        48     2048
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  

```

---

### Post by mickee384 on 2015-03-25
But I am still getting a weird refresh type issue on you tube. After running this stuff, is there a place to now configure it?

---

### Post by mickee384 on 2015-03-25
So now after all this, I think the issue is in Chrome. Poor playback of videos all choppy, like refresh lines. I am using the pepper flash. I've tried disabling that and the issue is still there, which is why I figured its a video driver issue. Everything other than chrome works great. Sorry if I sent you on a goose chase.

---

### Post by Yellow Pasque on 2015-03-25
You can look at "chrome://gpu" (enter that in the URL bar) and see your GPU status. Then you can look at "chrome://flags" and try enabling GPU override (it was the first option for me), relaunch the browser and check "chrome://gpu" again. Any difference?

---

### Post by mickee384 on 2015-03-26
That totally fixed it!!! Thanks soooolo much!!! Was no hardware acceleration!

---

### Post by mickee384 on 2015-03-26
computer froze overnight. Temüjin is there a way to undo the vdpauinfo part?

---

### Post by Yellow Pasque on 2015-03-26
> **mickee384 said:**
> computer froze overnight.
Doing what? Idling?

> is there a way to undo the vdpauinfo part?
You could remove the mesa-vdapu-drivers package, but why do you think that has anything to do with your system freezing?

EDIT: Also, if you remove VDPAU support, I think Chrome will go back to unaccelerated video playback...

---

### Post by mickee384 on 2015-03-26
ah, I see. I am not sure that is it, but with the nouveau driver It never froze. I will monitor and see how it does today. Thanks for replying!

---

### Post by mickee384 on 2015-03-26
Sorry, yes, must have been idling - happened while I was asleep. Only thing running at that time is Thunderbird

---

### Post by Yellow Pasque on 2015-03-26
>  but with the nouveau driver It never froze... Only thing running at that time is Thunderbird 

You're still using the nouveau driver (you simply added support for video decode acceleration using VDPAU). I'm not sure how the changes you made in this thread would cause your system to freeze, unless you were playing a video and/or running Chrome.

---

### Post by mickee384 on 2015-03-26
yep was completly frozen again :(

---

### Post by mickee384 on 2015-03-27
Eggzellent news. No freezing at all over 24hrs. Thanks for your help! Fingers crossed we are good to go!

---

### Post by mickee384 on 2015-04-02
Freezing was related to gdm being installed side by side with lightdm. I removed gdm

---

