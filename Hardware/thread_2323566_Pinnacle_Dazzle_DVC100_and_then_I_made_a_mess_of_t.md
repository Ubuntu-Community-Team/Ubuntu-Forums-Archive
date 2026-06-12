---
title: "Pinnacle Dazzle DVC100 and then I made a mess of things with V4L-DVB Drivers"
date: 2016-05-06
forum: Hardware
---

### Post by alforddm on 2016-05-06
So, in an attempt to capture some video I dug out my ancient Dazzle DVC100.   It was recognized by ubuntu with lsusb and after doing some googleling was able to get it to work with 

```
mplayer tv:// -tv driver=v4l2:width=720:norm=PAL:audiorate=48000:imm ediatemode=0:forceaudio:alsa:adevice=hw.2,0:device =/dev/video1:input=0 -vf pp=lb
```  (found in an old thread).  

and guvcview However, the video was only black and white and, while VLC could see the device,  it would never actually play any of the inputs just display a black screen.  

So, in an attempt to get things working better.  I followed this guide [https://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](https://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) to down load, make, and install V4L-DVB Device Drivers.    Now, not only is the Dazzle only recognized as an audio device, my webcam on the laptop isn't recognized either.   

It's entirely possible that the dazzle was broken when I started but I would like to get my webcam working again.  

Can anyone help me figure out what I messed up?  I'm using ubuntuGnome 16.04.

---

