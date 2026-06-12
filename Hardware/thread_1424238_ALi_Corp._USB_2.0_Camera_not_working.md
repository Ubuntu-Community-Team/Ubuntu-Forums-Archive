---
title: "ALi Corp. USB 2.0 Camera not working"
date: 2010-03-07
forum: Hardware
---

### Post by ugarth on 2010-03-07
Hi gentlemen.
I'm having a hard time with my laptop builtin webcam.

Up until a couple days ago it was working perfectly, but then I upgraded the kernel normally and the webcam stopped working in all kernels versions I had installed so I thought it might be a configuration problem.

I ended up downloading the latest version of the uvcvideo driver, compiled it and installed, as explained in [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) , but the problems remains. 

Technical details: I'm on kubuntu 9.10 and ```
$ uname -a
Linux aaaaaa 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
$ lsusb
(...)
Bus 002 Device 002: ID 0402:5606 ALi Corp. USB 2.0 Camera
(...)
```

"$ sudo lsusb -v -d 0402:5606" gives
[ATTACH]149340[/ATTACH]

After adding in /etc/modprobe.d/uvcvideo.conf
```
options uvcvideo trace=255
```
"dmesg | grep video" after booting shows
[ATTACH]149338[/ATTACH]

If I start luvcview
```
$ luvcview
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: MJPG
  Frame size:   640x480
  Frame rate:   30 fps
```then it just renders a black window and I have to kill it, but meanwhile the following is dumped to the system log (dmesg | grep video)
[ATTACH]149339[/ATTACH]

The camera seems to be mounted on /dev/video0 but camorama tells there is no such device. Skype and any other programs can't access it. Cheese just renders static.

So, it seems it's well detected and mounted, but no program can access it.

Thank you in advance for your help :)

---

### Post by ugarth on 2010-03-09
Of possible interest```
$ xawtv -hwscan                  
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.31-20-generic)
looking for available devices                                       
port 280-311                                                        
    type : Xvideo, image scaler                                     
    name : NV17 Video Texture                                       

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2                                                
    name : USB2.0 Camera                                       
    flags:  capture                                            

$ xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.31-20-generic)
xinerama 0: 1680x1050+0+0                                           
WARNING: No DGA direct video mode for this display.                 
/dev/video0 [v4l2]: no overlay support                              
v4l-conf had some trouble, trying to continue anyway                
Warning: Missing charsets in String to FontSet conversion           
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,           -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,          -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*,*" to type FontSet                             
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct                                                                                                                                                 
Warning: Missing charsets in String to FontSet conversion                                                                                                                                                                                    
Warning: Cannot convert string "-*-lucidatypewriter-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,           -*-courier-bold-r-normal-*-14-*-*-*-m-*-iso8859-*,          -gnu-unifont-bold-r-normal--16-*-*-*-c-*-*-*,        -efont-biwidth-bold-r-normal--16-*-*-*-*-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-m-*-*-*,                 -*-*-bold-r-normal-*-16-*-*-*-c-*-*-*,                         -*-*-*-*-*-*-16-*-*-*-*-*-*-*, *" to type FontSet                            
ioctl: VIDIOC_G_STD(std=0xb76ff1d000597326 [PAL_B1,PAL_G,PAL_D,PAL_M,PAL_N,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_H,SECAM_K,SECAM_L,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument                                                                                                                                                                                             
ioctl: VIDIOC_S_CTRL(id=9963778;value=2): Input/output error                                                                                                                                                                                 
ioctl: VIDIOC_S_CTRL(id=9963776;value=49): Input/output error                                                                                                                                                                                
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument                                                                                                                                                                                            
v4l2: oops: select timeout                                                                                                                                                                                                                   

**<FREEZE>**
```

---

### Post by d.tamm on 2010-03-22
I am having exactly the same problem and behaviour on Gnome (Karmic). Camera stopped working, likely after a kernel upgrade from 2.6.31-19 to 2.6.31-20.

```
$ lsusb 
...
Bus 001 Device 002: ID 0402:5606 ALi Corp. USB 2.0 Camera
...
```

```
$ uname -a
Linux ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
```

Would be great if anyone could come with a suggestion so I get back my camera.

---

### Post by tonyschmidt on 2010-03-28
I'm having the same issue.  Upon the upgrade to 2.6.31-20 my cam stopped working with skype on my System76 panp5.  So far the best solution seems to be to go back to booting into *-19.

---

### Post by samalex on 2010-07-30
Hey guys --

Sorry to bring back to life a 4 month old post, but I'm having the same problems on my PanP5.  I've documented what I've done on [this post]("http://ubuntuforums.org/showthread.php?p=9657213") on the System76 forum.

By any chance did you guys come-up with a work around?  Thanks -

Sam

---

### Post by tonyschmidt on 2010-07-30
my problem turned out to be camserv, upon uninstalling it all is working well again with skype.

---

### Post by samalex on 2010-07-30
> **tonyschmidt said:**
> my problem turned out to be camserv, upon uninstalling it all is working well again with skype.

Thanks for the quick reply, but this may be a different problem then I'm having since I don't have camserv installed :-/

Sam

---

### Post by d.tamm on 2010-08-11
I solved my problem (see my last post) by having my camera chip replaced: The chip was apparently broken, and fortunately had warranty on my computer :-)

Unfortunately, this will not be very helpful for the others of you...

---

