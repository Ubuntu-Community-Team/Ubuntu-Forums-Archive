---
title: "Quickcam Express confusion."
date: 2009-11-14
forum: Hardware
---

### Post by brandonsh on 2009-11-14
Hello!
I have a Quickcam (Express?) webcam. I'm not sure what model number it is, but it is beige and is a round ball with a triangle stand. Cheese says no webcam detected, so I read some guides and they didn't say much except to run dmesg. I did that and got this:

```
[   13.428386] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   13.428396] quickcam: Kernel:2.6.28-16-generic bus:1 class:FF subclass:FF vendor:046D product:0840
[   13.434311] quickcam: Sensor HDCS-1000/1100 detected
[   13.436663] quickcam: Registered device: /dev/video0
```

So I see no reason why it wouldn't be working.
Any ideas?

Thanks,
BrandonSH.

---

### Post by Butter1 on 2009-11-15
Hi, 

I've got the same problem when I tried my webcam yesterday (Logitech quickcam express).
I get it working in camorama if I enable access to /dev/video0 by sudo chmod 666 /dev/video0 but the picture is horrible. But at least it is a picture as a prof that it should be possible to get this piece working. 

But no lock with luvcview, cheese or VLC.

Some one else experienced with similar problems solved?

Regards, P

---

### Post by brandonsh on 2009-11-19
Bumpy Bump.

---

