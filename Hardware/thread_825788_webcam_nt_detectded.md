---
title: "webcam nt detectded"
date: 2008-06-11
forum: Hardware
---

### Post by bkamalnivas on 2008-06-11
ubuntu detects my USB drive bt nt my webcam ....please help

---

### Post by linuxwizard on 2008-06-11
Post the complete results of the command > lsusb

---

### Post by barney385 on 2008-06-14
barney@barney-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b018 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 147e:2016  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
barney@barney-laptop:~$

---

### Post by linuxwizard on 2008-06-14
barney385
Have you tried using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by PaulAnka on 2008-06-14
I have the same problem.
```

frak@frak-laptop:~$ lsusb
Bus 005 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c51b Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

I installed [EasyCam]("https://help.ubuntu.com/community/EasyCam") and launched it. I tried every device, but nothing happens.
Is there some other way to make my webcam work?

Thanks for the help. :)

---

### Post by linuxwizard on 2008-06-14
PaulAnka
Have you tried using Ekiga to see if your webcam will work ? Alot of webcams will just work.

---

### Post by PaulAnka on 2008-06-14
Yes, I tried using Ekiga, but it doesn't detect any video devices.
I'd actually use the webcam with Skype 2.0 but it has the same problem: no video devices detected.

I also tried Camorama, but it says it couldn't connect to the device.

---

### Post by KemKev on 2008-06-14
We may be banging our heads against the wall.  From what I've seen so far, there are no native webcam drivers in Huron, and some of the the generic drivers will only compile on kernels up to 2.6.22.  Problem is, Hardy's kernel is 2.6.24, so they won't work there.  Apparently, the Linux headers changed names in Hardy so unless there's an upgraded UVC (or some other) driver that works with Hardy's kernel, we seem to be up the creek without a paddle.  One person got it working by downgrading Hardy's kernel, but that sounds like a lot of work, especially for a newbie like me.

---

### Post by PaulAnka on 2008-06-14
That's a pity.
I guess I'll have to use Windows when I want to use my webcam.
Thansk for your help anyway.

---

### Post by barney385 on 2008-06-14
Ekiga is not an option for me. I have the softphone option only and no other is available through synaptic. Maybe because I'm using the 64-bit OS.

Anyway, I tooled around and got it working. 

Thanks though. 

That was the only issue I've had with Hardy since installing...

:smile:

I'll tell you what I did in synaptic after this download is done. I did a search for webcam drivers and found the files I needed, then used cheesey to view.

---

### Post by linuxwizard on 2008-06-14
PaulAnka
I always suggest testing a webcam with Ekiga first before trying to installing a driver, because alot of webcams will just work. Now looking more at your webcam > ID 0402:5602 ALi Corp. Video Camera Controller > no driver yet for your cam.

The built-in webcam, which is an ALi 5602, does not have a functioning Linux driver yet. There is, however, one in development, which I tried downloading and installing. And although something does happen and the driver seems to recognise the camera, it does not work. 

[http://sourceforge.net/projects/m560x-driver/](http://sourceforge.net/projects/m560x-driver/)

---

### Post by KemKev on 2008-06-16
> **PaulAnka said:**
> That's a pity.
I guess I'll have to use Windows when I want to use my webcam.
Thansk for your help anyway.
I found a solution that worked for my webcam, and posted it in the thread linked below:

[http://ubuntuforums.org/showthread.php?t=829203](http://ubuntuforums.org/showthread.php?t=829203)

If your cam use the r5u870 driver, it might be worth a try.

---

### Post by stchman on 2008-06-16
> **bkamalnivas said:**
> ubuntu detects my USB drive bt nt my webcam ....please help

Install Cheese, it is a webcam program.

---

