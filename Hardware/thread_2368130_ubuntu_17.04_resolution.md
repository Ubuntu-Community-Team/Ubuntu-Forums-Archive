---
title: "ubuntu 17.04 resolution"
date: 2017-08-07
forum: Hardware
---

### Post by connor5591 on 2017-08-07
Hi, i've being troubleshooting for a really long time trying to get 1920x1080 (my native res) on ubuntu 17.04, it works fine on windows. im using a gtx 970 and a hdmi from my pc to monitor. at this point, i've come to the conclusion i need new cables. has anyone ever not being able to get their native res using a hdmi both ways? this is my monitor: [https://www.amazon.co.uk/ASUS-VE247H-Widescreen-Intelligence-Technology/dp/B004T2LMP2/ref=sr_1_1?ie=UTF8&qid=1502114579&sr=8-1&keywords=ve247h](https://www.amazon.co.uk/ASUS-VE247H-Widescreen-Intelligence-Technology/dp/B004T2LMP2/ref=sr_1_1?ie=UTF8&qid=1502114579&sr=8-1&keywords=ve247h) i was thinking of trying dvi to hdmi.

---

### Post by #&amp;thj^% on 2017-08-07
Works fine here,
```
inxi -G
Graphics:  Card-1: Intel HD Graphics 530
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: x11 (X.Org 1.19.3) driver: nvidia
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 560 Ti/PCIe/SSE2
           version: 4.5.0 NVIDIA 384.59

```
Lets see how your system sees it:
Post back the return of this from the terminal:
```
xrandr -q

```
Mine shows this
```
xrandr -q
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
DVI-I-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
  ** 1920x1080     60.00*+**
   1680x1050     59.95  
   1600x1200     60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       60.32  
   640x480       59.94  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected (normal left inverted right x axis y axis)
   1360x768      60.02 +
   **1920x1080     59.94    60.05    60.00  **
   1440x480      60.05  
   1280x720      60.00    59.94  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    60.32  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DVI-I-3 disconnected (normal left inverted right x axis y axis)


```
Also do you have the Nvidia Driver installed?

---

### Post by connor5591 on 2017-08-07
yep, im currently not on ubuntu though. but i went through all that xrandr troubleshooting to no avail. although mine was connected through HDMI-0 and DVI was disconnected, and the max resolution i saw was 1300x768. are you using DVI to HDMI right now? I'm using a hdmi cable both ways.

---

### Post by #&amp;thj^% on 2017-08-07
> **connor5591 said:**
> yep, im currently not on ubuntu though. but i went through all that xrandr troubleshooting to no avail. although mine was connected through HDMI-0 and DVI was disconnected, and the max resolution i saw was 1300x768. are you using DVI to HDMI right now? I'm using a hdmi cable both ways.

Yes I have dual GPU's but both work with dual HDMI @1920 x 1080
I also test newer releases currently 17.10 with wayland and i need to HDMI to Intel for that. (Hope that dose not confuse you further) 
But when you get back on Ubuntu we can check a few things...when your ready.;)
You say you have the Nvidia Driver installed you could check through Nvidia-Settings for more Options.

---

### Post by connor5591 on 2017-08-07
yep they were 100% installed but ill reinstall ubuntu and give it another go in a few hours :)

---

### Post by connor5591 on 2017-08-07
getting this error now before i even get into ubuntu. this is after i click ubuntu on the terminal menu before the OS Starts.
i'd like to add as well while im frozen on this black screen i can hear ubuntu launching in the background.

---

### Post by Autodave on 2017-08-07
Do you remember installing an Nvidia driver? If so, where did you get the driver from?

---

### Post by connor5591 on 2017-08-07
nope, this is a fresh install. but the last time i gave ubuntu a try i was using the nvidia proprietary driver (375.66) it partially worked as i could only pick up 800x resolution, and then after i was able to get 1300x. this error im getting now was solved by a fix i found, typing nomodeset in the editing prompt by clicking e on ubuntu at the start up, but figured its probably best not to do that again this time since this error could be preventing me from picking up my native res

---

### Post by #&amp;thj^% on 2017-08-07
Ok I'll bet you did not format the new install then.
Run this one line at a time and hit enter after each .
```
cd /etc/X11
ls
```
paste back so we can see

---

### Post by connor5591 on 2017-08-07
sorry but how do i type that? i get that error i posted above before i can even install : )

---

### Post by #&amp;thj^% on 2017-08-07
> **connor5591 said:**
> sorry but how do i type that? i get that error i posted above before i can even install : )

Well I did not see that till just now.;)
Did you have problems installing it (The operating system and not the Driver) the first time?

---

