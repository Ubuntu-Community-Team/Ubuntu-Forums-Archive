---
title: "Intel cs330 on 8.10 or Fedora 10"
date: 2008-11-27
forum: Hardware
---

### Post by DouglasAWh on 2008-11-27
I mostly use Ibex, but I installed Fedora 10 to see if maybe it would work better with my webcam and wacom, neither of which I can get to work.  I'm about to give up on both.  Anyway, I've seen that there are drivers for my webcam ([http://www.compatdb.org/support/topics/25685_intel_pro_cs430_usb_cam_vs_non_pro_usb_cs330_cam.html](http://www.compatdb.org/support/topics/25685_intel_pro_cs430_usb_cam_vs_non_pro_usb_cs330_cam.html)) but I can't see where to download them.  I've also seen that these forums have failed to help people on this issue in the past: [http://ubuntuforums.org/showthread.php?t=366362](http://ubuntuforums.org/showthread.php?t=366362).  I'm hoping for a better response this time.  Thanks!

---

### Post by cariboo on 2008-11-27
That link you provide is for Windows drivers. If you think windows drivers might work have you tried using them with ndiswrapper?

Check here:

[http://www.linux-drivers.org/usb_webcams.html](http://www.linux-drivers.org/usb_webcams.html)

for drivers for your web cam or

check the output of lsusb then go here:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

to see if there is a driver.

Jim

---

### Post by DouglasAWh on 2008-11-27
Thanks for pointing that out.  I wonder why they were having to "hack" Windows drivers.  The default drivers worked fine for me on Windows.  I'll report when I've had a chance to look at those links.  Thanks!

---

### Post by DouglasAWh on 2008-11-27
Looks like my video quality is going to be bad no matter what. :(

> 
ViewQuest 	79 	0x0733 	0x0401 	Create and Share 	CS330 	spca501a 	  	Yes 	yuyv 	spca5xx 	*


---

### Post by DouglasAWh on 2008-11-27
all I can find through Synaptic and apt are gspca-source.  Does this mean I'll have to compile this to get my video card working?

---

### Post by albertz on 2009-05-12
Bump. What about this gspca-source. How can I use it?

---

