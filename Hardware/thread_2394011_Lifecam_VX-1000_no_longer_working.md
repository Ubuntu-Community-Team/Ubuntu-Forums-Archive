---
title: "Lifecam VX-1000 no longer working"
date: 2018-06-11
forum: Hardware
---

### Post by HereInOz on 2018-06-11
Hi All,

Since upgrading to 18.04, the Microsoft Lifecam VX-1000 which used to work in 17.10, has ceased functioning.  It still reports in lsusb: Bus 003 Device 003: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000, but Cheese, Skype, etc cannot detect it. 

I have plugged the camera in to a 16.04 machine I have and it is fine in that one, so nothing wrong with the camera.

It looks like the driver has, for some reason, been removed from the 4.15 kernel.  Has anyone else found this, and is there a workaround?

Hope you can help.

---

### Post by Autodave on 2018-06-11
Desktop or laptop?

Did you upgrade or do a clean install?

---

### Post by HereInOz on 2018-06-11
Desktop or Laptop?  Both.  The camera is on my desktop, but I have also tried, without success, to get Cheese to see it on a laptop running 18.04.  A laptop running 16.04 has no problems.

The systems in question were upgrades from 17.10 to 18.04.  I may try a clean install and see what goes.

---

### Post by Autodave on 2018-06-12
I would first try booting the machine off of the install medium. If the camera works that way, there is a very good chance that it will work in the in stall.  Personally, (and others here will back me and also disagree with me) I have never had much luck doing an upgrade: I have learned to just do a new install: saves much time in the long-run.

---

### Post by HereInOz on 2018-06-12
Thanks for the info.  I booted off the installation USB medium - no good.  I ran up a new clean install on an HP machine I had in the corner and still no joy at all.  I tested the camera straight after the install with no luck and then updated the system with the updates since release and still no good.  So the problem is not the upgrade from 17.10, and it is not the camera, for it works on 16.04 and worked on 17.10.  

I reckon that the driver has been omitted from the kernel.  They did something like this with the 4.13 kernel (17.10) where they messed up the drivers for the video in the Intel 914 chipset.  914 video support magically re-appeared in the 4.15 kernel.

Probably worth submitting a bug report.

---

### Post by $yl9pAR%t on 2018-06-12
Before you start blaming kernel, try to use Camorama instead Cheese.

---

### Post by HereInOz on 2018-06-12
Ah, now that shows me an image.  Interesting.  Thanks for that.  I will now check out how it works on Skype, etc.

---

### Post by HereInOz on 2018-06-12
The camera still cannot be found by Skype, but the fact that Camorama can see it indicates that the problem is other than a kernel driver.

Ahh, the joys!!

---

### Post by br116 on 2018-06-20
I'm having the same issue with the VX-3000. No image on Skype, Cheese nor Camorama. Camera light continues steady but I can't find the process using it. Noticed that not all USB ports acknowledge the camera either, but lsusb lists it ALL the time.

---

### Post by HereInOz on 2018-06-23
That is an interesting one about the USB ports.  I have a couple of laptops, 1 running Ubuntu 18.04 and the other running Ubuntu Budgie 18.04, with a virtual machine of Windows 10 running on them.  I will see what happens when I try to connect the USB Camera through VirtualBox to the Windows machines.

---

### Post by HereInOz on 2018-06-24
Doh!  There is no MS driver for that camera for Windows 10 either.  I give up.

---

### Post by br116 on 2018-07-25
Perhaps to finalize my ends to this......
I re-installed 18.04 from scratch (not from 16.04 as before) and the camera (and all USB ports) now work with Camorama only. No luck with VLC not Cheese. :(

---

### Post by martin.komara on 2018-08-19
This works for me:
```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so cheese 
```

---

