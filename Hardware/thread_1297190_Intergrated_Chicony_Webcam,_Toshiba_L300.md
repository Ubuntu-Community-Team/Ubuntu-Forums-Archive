---
title: "Intergrated Chicony Webcam, Toshiba L300"
date: 2009-10-21
forum: Hardware
---

### Post by Shamsul007 on 2009-10-21
er, so ive installed ubuntu 9.04 on this laptop, it came with vista but wanted to try out ubutu instead, 

anyway this is what lsusb says

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

its an intergrated webcam, so im wondering if theres anyway to make it work?

---

### Post by Giblet5 on 2009-10-21
Have you installed an application that uses a webcam?

OpenOffice and Firefox don't have much use for one. ;)

(My integrated Chicony webcam works fine if I bring up a webcam program.)

---

### Post by Wistful on 2009-10-30
I have a similar integrated webcam : 
Bus 002 Device 003: ID **_04f2:b044_** Chicony Electronics Co., Ltd

And when I want to access it within **Camorama** it outputs this error:
"Could not connect to video device (/dev/video0/). Please check connection."

However after upgrading my system to Karmic Koala 9.10(kernel 2.6.31-13-generic) and installing **Cheese*****(_sudo apt-get install cheese_) everything seems to work fine.

From the information derived from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) your **_04f2:b070_** Toshiba Satellite L350D notebooks Chicony Electronics webcam is supported as well as mine.

> Linux 2.6.26 and newer includes the Linux UVC driver natively. You will not need to download the driver sources manually unless you want to test a newer version or help with development.

Notes:
*Cheese is a cheesy program to take pictures and videos from your webcam. It also provides some graphical effects in order to please the users play instinct.
->If someone else encounters problems with their webcam, check these sites to see if your cam is supported and download/build the proper driver:
1) [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
2) [http://linux-uvc.berlios.de](http://linux-uvc.berlios.de) (already hyperlinked above)
3) [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
4) [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

To see the vendor ID and Name of manufacturer, open a Terminal emulator and type : **lsusb**

---

### Post by nicocarbone on 2009-11-01
I have the same (or very similar) Chicony webcam on my Toshiba M305 laptop. It worked nice on Jaunty, but it doesn't work in Karmic. When I open Cheese, the camera tuns on for a few seconds (at least, the camera activity led turns up) and then it turns off completely. After this, Cheese shows the calibration picture. 

I tested the camera in MSN client Emesene, and it doesn't work either (it worked perfectly on Jaunty).

It seems like a bug, but I am not sure which package to blame, so I don't know where to post this regressing bug. 

Any ideas? Thanks,

---

### Post by acidbits on 2009-11-08
* bump *

Same here. Toshiba laptop with integrated webcam (lsusb):

```
Bus 002 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
```

Any program that uses the webcam only gets the image the first second or so, then black image. Tested with cheese, luvcview and vlc,

Looks like an uvcvideo problem, I'm not skilled enough to go any further,

Webcam worked flawless with previous ubuntu release, problem appeared after upgrading to 9.10.

---

### Post by sirwhiteout on 2009-11-20
I have a similar problem , but instead of just not working, whenever I open a program which uses the webcam (Cheese, Skype), all my USB devices just stop working a few seconds later.

In particular, the devices which I immediately notice stop working are:

```
Bus 001 Device 005: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 005 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
```

These are all internal devices.

This started happening after I upgraded to Karmic, as well. Bug report, anyone?

---

### Post by trigeorgis on 2010-01-01
Has anybody figured out a solution for this problem? I have the same problems as your guys...

---

### Post by nicocarbone on 2010-01-01
In my case it was solved by some automatic update. I am not sure exactly which one, but I think it was one of the kernel updates. It works perfectly now.

---

### Post by F1r3fly on 2010-01-01
Juste submitted a bug report.
As I didn't know on which package post it, I guess Cheese guys know about webcams ;)
Bug report available @ [https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/502222](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/502222)
I also linked this thread for devs x)

---

### Post by mac1984user on 2010-01-13
I have the Toshiba L300D and am having a similar issue of the webcam not working under 9.10 (worked fine in Vista - but who wants Vista?). Certainly hope there's news on this soon. Cheers!

---

### Post by taygan on 2010-02-12
It might be a kernel problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/462336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/462336)

I tried installing 2.6.32, on a Gateway M-1625 but then my wireless broke.  The new kernel will be in 10.04.  Anyone figure out a workaround for the time being?  Or how to get wireless and 2.6.32 working on Karmic?

---

### Post by Tom_T on 2010-05-20
Did anyone ever get this sorted ?

We're having a similar issue with 10.04 & a L300 Web cam.
Although it did seem to work at first.. now it doesn't !!

---

### Post by i_love_lucidlynx on 2010-05-27
Hi,
I am a toddler in terms of Ubuntu.. So, I am not really sure where I should be posting my query.. I found this to be the nearest one.. So....
I have a toshiba L510 laptop which came with DOS pre-installed.. Till now, I was running Win7 and Ubuntu 9.10 (wubi) on dual boot.. Things were going pretty well until I upgraded to 10.04.. I mean, it was working fine but I was fiddling around a lot and that messed up the grub.. But still, I liked 10.04 so much so that I formatted and did a clean install of 10.04.. My webcam was working fine with all the applications like cheese, skype, vlc etc on 9.10 initially and 10.04 also, when I upgraded, but after the clean install, it doesnt seem to be working.. It works with vlc, but not with any other app.. I tried cheese, skype, ekiga and camorama.. the details of the webcam are-

[SIZE=3]Bus 001 Device 003: ID 04f2:b120 Chicony Electronics Co., Ltd [/SIZE]

Not that i really need the webcam, but it would be great if it worked.. Also, the Fn key does not work.. I do not have dedicated keys for bluetooth and wi-fi.. its a single key for both (F8 ) coupled with Fn.. I had kept both turned on in windows before i started the installation, hence its working..

Any help in both the queries mentioned above will be greatly appreciated..

Sid..

---

### Post by lisati on 2010-05-27
Hmmmmmm.... I'm stumped. Clean install of 10.04, 64-bit, mine works.

---

### Post by i_love_lucidlynx on 2010-05-28
I dunno how it happened or what i did, but my cam seems to be working now.. atleast with cheese.. the last few things i did was, i removed cheese (as i had installed it from software centre).. Den, i did all the updates and installed kde4.. lastly, i used _'sudo apt-get install cheese'_ and installed cheese again.. Now it works..

---

### Post by abdusamed on 2010-06-08
the camera is working but the darkness issue remains. If having a video conferencing on skype, the webcam image goes completely dark. I think i might have found the solution. The solution was lowering the frame rate of the video being capture through guvcview. I did what Toshiba original software does on windows it simply reduces the framerate [not resolution] to brighten up the video and yes it works. But i can't seem to change the setting of the webcam so it always uses that framerate setting because in normal 30fps the video becomes really dark and dirty but smooth. The question arises how can we change permanently the resolution of the video to a lower setting? If that works... i'm pretty surre it would be helpful to many other people facing the similar problem.

---

### Post by meditatingfrog on 2010-11-06
i have a toshiba u305-s7448, and i can get cheese to record video on the Chicony webcam, but there is no audio recording.  i think i need an updated driver for the Chicony webcam.  not sure where to get it, looks like i'll be googling tonight.

---

