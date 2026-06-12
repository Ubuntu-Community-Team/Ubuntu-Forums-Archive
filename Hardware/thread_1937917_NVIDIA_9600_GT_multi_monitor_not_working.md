---
title: "NVIDIA 9600 GT multi monitor not working"
date: 2012-03-08
forum: Hardware
---

### Post by link15 on 2012-03-08
I just built a computer with:
ASUS P5N-D motherboard
1TB western digital hard drive
8GB of memory
NVIDIA GEForce 9600 GT (its the PNY one)
I installed ubuntu 12.04 beta 1 64bit no problem and multi monitor worked in the livecd but after it finished installing I restarted and in the install I opened displays and says unknown (I've tried the additional drivers app) I'm including a screenshot of the displays window to help BTW unity 3d works PERFECTLY, any suggestions? (sorry if that didn't make much sense)[IMG]/home/scooter/Pictures/Screenshot from 2012-03-08 16:11:01.png[/IMG]

---

### Post by papibe on 2012-03-08
Did you installed the proprietary driver? (I would recommend it BTW)

If so, you have to use 'Nvidia X Server Settings' to set up your monitors.

Note that your pics didn't upload properly.

Regards.

---

### Post by druid23 on 2012-03-08
is nvidia-settings available?

I've used that motherboard and graphics chipset without problem for multi-monitor before, not tried with 12.04 beta. always used nvidia-settings to configure multiple monitors.

---

### Post by link15 on 2012-03-08
> **druid23 said:**
> is nvidia-settings available?

I've used that motherboard and graphics chipset without problem for multi-monitor before, not tried with 12.04 beta. always used nvidia-settings to configure multiple monitors.
where do I get nvidia-settings?
> **papibe said:**
> Did you installed the proprietary driver? (I would recommend it BTW)

If  so, you have to use 'Nvidia X Server Settings' to set up your monitors.

Note that your pics didn't upload properly.

Regards.

1. how do I get the Nvidia X server Settings
2. I installed the "Nvidia accelerated graphics card (post release updates
3.thanks for the quick reply

---

### Post by link15 on 2012-03-08
ok I found NVIDIA-settings and I set it to dual monitor except now it is in unity 2d instead of unity 3d does anyone have any suggestions?

---

### Post by papibe on 2012-03-08
You can select the session (3D or 2D), at login time. Check this youtube [video]("http://www.youtube.com/watch?v=CBnMavycA6I") (0:32). 

Hope that helps, and tell us how it goes.
Regards.

---

### Post by link15 on 2012-03-08
I already tried that, no luck :( I'm gonna reinstall and try again, wish me luck :D

---

### Post by link15 on 2012-03-09
ok I just finished reinstalling, no luck :( any other suggestions?

---

### Post by link15 on 2012-03-10
YAAAY!!!! I GOT IT TO WORK!!!!! [http://ubuntuforums.org/showthread.php?t=1859730&page=3](http://ubuntuforums.org/showthread.php?t=1859730&page=3)

---

