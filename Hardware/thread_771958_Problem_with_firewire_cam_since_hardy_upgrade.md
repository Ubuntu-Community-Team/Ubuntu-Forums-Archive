---
title: "Problem with firewire cam since hardy upgrade"
date: 2008-04-28
forum: Hardware
---

### Post by mwerlberger on 2008-04-28
Hi!

I did an upgrade to hardy and since then i have a problem to get an image from my IEEE1394 Point Grey Research Firefly MV FFMV-03MTM (just a simple industry firewire cam). I do all my testing with coriander and use the cam with some C++ programs. When i try to receive an image within coriander i get an '(dc1394_capture.c:466) error!'. As method i have raw1394 and /dev/raw1394 is there when i plug in the cam.

This worked all great in Gutsy before. Does anybody has a hint how to get the cam working. It is very important for me because i should finish some work in the next 2 week and therefore need the cam.

Thx for any idea.
Regards,
 Manuel

---

### Post by mwerlberger on 2008-04-28
me again. I just installed coriander 2 rc6 to test if it has something todo with the libs. Therefore i had to install a new version of libdc1394 (2.0.1) and some other deps. Coriander shows an image. I will do some testings with my libs and reply again for some issues.

Hope that somebody might find this thread if running into the same troubles. Would be interesting what changed within the libs that everything worked great with Gutsy and got broken within Hardy? Some ideas?

Rgds,
 Manuel

---

### Post by RalphP on 2008-04-29
Try:
sudo chmod a+rw /dev/raw1394 
as referenced in:
[http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html](http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html)

This is a problem with all users not having permissions against the raw1394 device. Fixed my problem right away. Good luck.

---

### Post by mwerlberger on 2008-04-29
> **RalphP said:**
> Try:
sudo chmod a+rw /dev/raw1394 


This should not be necessercy if the user is in the disc and video group. Was working at least with Gutsy without a problem. Now after the upgrade to Coriander 2 at least getting an image with Coriander works (for root and users that are in the above mentioned groups). But i have still problems with the libs i am using in my c++ program. But i had not the time to go into the depth and check the lib dependencies yet. Will do that the next days.

If somebody is reading this and uses a firewire cam in a C++/C program. How to you do that? (I don't want to integrate OpenCV or sth like this - i would like to prefer a small(!) lib or just a header like the boost stuff or something....).

Regards,
 Manuel

---

### Post by tk03759 on 2008-04-30
> **RalphP said:**
> Try:
sudo chmod a+rw /dev/raw1394 


this worked for me. same problem after hardy upgrade.
i read it needs to be done after each restart though? i'll repost after a restart.

---

### Post by mwerlberger on 2008-05-01
Try to add your user to the disk and video group and the chmod should not be needed.

---

### Post by mwerlberger on 2008-05-05
Ok hears the deal: After the upgrade i had some problems with the libs i installed. Therefore i did a new installation to test the camera stuff. Receiving an image from the cam over video1394 works great. But as i want to use the libdc1394 api for my program i have to read the image from raw1394. When i do this within coriander (1.0.1) i get the error
```
(dc1394_capture.c:466) error!
```

dmesg | tail says:
```
[ 8312.197932] raw1394: old iso ABI has been removed
```

Does anybody has an idea how to fix this? Is there a bug within the current libs of Hardy??

Regards,
 Manuel

---

### Post by AntoniaLY on 2008-11-18
Has anyone a solution for this problem? Firewire Camery is not working on raw1394 via coriander. And I need it working for my C++ Program.

Thanks,
Antonia

---

