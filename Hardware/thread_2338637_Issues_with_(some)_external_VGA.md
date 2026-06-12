---
title: "Issues with (some) external VGA"
date: 2016-09-30
forum: Hardware
---

### Post by gianluca3 on 2016-09-30
Hello,

following my post: ([https://ubuntuforums.org/showthread.php?t=2305302](https://ubuntuforums.org/showthread.php?t=2305302)) I'm experiencing now different problems still with external VGA (that's why another thread).

I'm testing the Dell DisplayLink, an adapter connecting the laptop USB port with USB, ethernet, HDMI and VGA. I downloaded the driver from: [http://www.displaylink.com/downloads/ubuntu](http://www.displaylink.com/downloads/ubuntu)

The device works fine on my desk, when I go in the classroom and try to connect with the VGA-based projector it simply output a blank screen. If I check on the connected devices the system recognizes the additional screen and, apparently, no problem arise.

I read somewhere, and noticed that it is experimentally true in my case, the problems arise when the VGA cable is "long". I understood the issue with the minidisplayport device, since the second screen was not even recognized, but in this case? 

Any help? 
I'm far to be an expert but I have to say that this uncertainty in ah hardware or software problem is affecting my trust in both the hardware (Dell) and the software (Ubuntu).

Thanks
g.

```

uname -a
Linux drogo 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

lspci
...
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)

```

---

