---
title: "error installing NVIDIA drivers"
date: 2015-09-22
forum: Hardware
---

### Post by Zombir on 2015-09-22
Dear all,

I am relatively new to Linux and I have Ubuntu 14.04 installed on my laptop (Dell Inspiron N5110 ) . I want to do some OpenCL programming so decided to install the proprietary Nvidia Drivers for my laptop. I get the following result for the command:

```
Inspiron-N5110:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 525M] (rev a1)

```

I tried the GUI method of installing drivers. After updating the OS to the newest version of softwares. I get the following list when I go to additional drivers:

```
Using NVIDIA binary driver - version 346.82 from nvidia-346 (proprietary,tested)
Using NVIDIA binary driver - version 340.76 from nvidia-340-updates (propretary)
Using NVIDIA binary driver - version 346.82 from nvidia-346-updates (propretary)
Using NVIDIA binary driver - version 340.76 from nvidia-340 (proprietary)
Using NVIDIA legacy binary driver - version 304.125 from nvidia-304 (proprietary)
Using X.Org.X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)
Using NVIDIA legacy binary driver - version 304.125 from nvidia-304-updates (proprietary) 

```

from that list, what is currently selected is the Nouveau driver. I tried selecting  ```
Using NVIDIA binary driver - version 346.82 from nvidia-346 (proprietary,tested)
``` (the first one ) and after rebooting I got a very low resolution display and the dash and the mouse pointer were missing. 

Does this mean that I installed the wrong driver ?
Or is it an error in my hardware ?
If I have installed the wrong driver, which one should I install out of the above list ?

Thank you for your help. 

Regards,
ZMBR

---

### Post by VMC on 2015-09-22
Go to this [link]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"), and under "Low/Missing Screen Resolutions", run the command as suggested. First though from terminal type this to see what resolutions you do have: *xrandr*

Also Nvidia does show GeForce GT 525M as supported for 346.82

---

