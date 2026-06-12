---
title: "Built-in webcam not working"
date: 2018-08-17
forum: Hardware
---

### Post by zk8lfer on 2018-08-17
Hi everyone! I have a Toshiba Satellite-L50-B, Intel® Core™ i3-4005U CPU @ 1.70GHz × 4, 64 bits... I uninstalled win 10 because it was causing me too many problems and fully installed ubuntu 16.04 LTS.

I was checking some stuff and realized my webcam wasnt working at all.. its a built in camera... I tried cheese but the screen of the webcam appears all black and no sign of life at all, then tried vlc and said: VLC unable to open [COLOR=#000000]MRL «v4l2://». 

I tried it in Chromium looking for a cam test but the pages i tried told me that webcam was not working properly.

when looking in the terminal for lsusb, I didnt find it :(

[/COLOR]skullcandy@skullcandy-Satellite-L50-B:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0930:0227 Toshiba Corp. 
Bus 002 Device 005: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I dont know if its that my webcam's driver its not installed or if I have to install it, either way I dont know how to do it

Please someone help me

---

### Post by mörgæs on 2018-08-18
Hi, welcome to the fora.

Does it work differently in a live boot of 18.04.1?

---

### Post by hgkrug1 on 2019-02-07
[SIZE=3][FONT=sans-serif][/FONT][/SIZE]I find that most post about webcams deal with USB linked webcams. I used Ubuntu 18.04 desktop and Cheese and Guvcview do not see the webcam. 

I have a HP EliteDisplay E273m27-inch Monitor with a build-in webcam. I can see a "Video bus" under input devices with the System Profiler and Benchmark app (hardware info).  

However, I have tried to find a way to search for the webcam detaisl from the command line.  When I usethe following command:

$ sudo lsmod | grep video

uvcvideo               90112  0

videobuf2_vmalloc      16384  1 uvcvideo

videobuf2_memops       16384  1 videobuf2_vmalloc

videobuf2_v4l2         24576  1 uvcvideo

videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo

videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo

media                  40960  2 videodev,uvcvideo

video                  45056  2 dell_wmi,i915  

I suspect the "videodev" is the build-in webcam.  Any idea how I can activate it?
Thanks! Gert Kruger

---

### Post by hgkrug1 on 2019-02-11
I also tried a USB webcam from Samsung on Ubuntu 18.04 desktop.  It still sees only the internal (I guess) using:

$ sudo lsmod | grep video

video                  45056  3 dell_wmi,i915,nouveau

Any one know how to either activate the internal or USB webcam?

Thanks!
Gert Kruger

---

### Post by hgkrug1 on 2019-07-18
Apologies!  The problem was I did not use the correct cable to connect my monitor.  There is still a problem with weak sound though, but the camera works!

---

