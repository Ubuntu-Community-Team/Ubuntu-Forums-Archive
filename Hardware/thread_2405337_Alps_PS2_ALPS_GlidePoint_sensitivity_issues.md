---
title: "Alps PS/2 ALPS GlidePoint sensitivity issues"
date: 2018-11-04
forum: Hardware
---

### Post by hsherif on 2018-11-04
Hey guys/girls,

I need your help, I've been rolling with Ubuntu 18.04 bionic beaver on my HP Pavilion 14-n202se laptop.

Everything is working great from the touch screen and everything.

However my touchpad is giving me a huge headache and I've search everywhere with no fix.

As showing on xinput the it's currently detected as "Alps PS/2 ALPS GlidePoint". I've having this issue where the touchpad doesn't recognize my input for a second, then it does afterwards. Sometimes the cursor moves normally, then sometimes very slow.

It's driving me nuts. Please let me know if you need any logs or stuff, but just let me know what to type in terminal cause I'm still fresh in this business. :)

Edit:  Weirdly it is working perfectly with Windows 10 VM within Ubuntu.....it must be the OS rather than the drivers in use??? possibly settings wise?

Thanks.

---

### Post by hsherif on 2018-11-13
After alot of research, I ended up using the synaptics touchpad driver and I must say it feels a lot better.

I had configured it with the synclient command to increase the sensitivity required to trigger the touchpad.

I'm gonna add the details here in hope that it will help someone someday:

Directly affecting sensitivity:

1. Set the FingerLow value to 1.  (Using command synclient FingerLow=1)
2. Set PressureMotionMinZ to 1.

Had to adjust my two finger horizontal scroll from HorizScrollDelta to -50.
Had to write a bash script to run on startup with these commands as the settings were never saved upon restart.

---

### Post by abhinav-5-jha on 2019-07-26
Hey I'm new to ubuntu and I'm facing the same problem could you give me terminal commands?

---

