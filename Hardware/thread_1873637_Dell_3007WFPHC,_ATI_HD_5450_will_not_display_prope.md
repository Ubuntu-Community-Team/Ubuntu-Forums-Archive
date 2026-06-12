---
title: "Dell 3007WFPHC, ATI HD 5450 will not display properly"
date: 2011-11-01
forum: Hardware
---

### Post by muddymudskipper on 2011-11-01
I have installed Ubuntu 11.10 on a Dell Optiplex 990, and cannot seem to get a resolution other than 1280x800 on my 30" monitor (Dell 3007WFPHC).  I am using a DMS-59 to DVI-DVI splitter cable.

I initially tried installing the proprietary ATI driver "FGLRX," and was not able to get the system to display the correct resolution (2560x1600) using the Display GUI, or using xrandr.  I was unable to install the proprietary driver "FGLRX update".

I tried installing 11.04 with the same result.

I am back on 11.10, and have stayed with the default open source driver, trying to get the video card/monitor to display at anything beyond 1280x800 with the xrandr utility.  When I set the output using xrandr, the screen will either turn black, or display colored garbage.  I have tried other supported resolutions like 1600x1000, 1920x1200, 2560x1600, with no success.

I have another 17" monitor hooked up to the other DVI output, and  ubuntu detects the supported modes just fine. I have tried disconnecting the 17" monitor to mess with the output using xrandr with no success.  I have also swapped the relative positions of the two monitors with no success (for instance moving the 3007WFPHC to DVI-0, and the 17" monitor to DVI-1).  I have also tried generating an xorg.conf file in my home directory and manipulating various settings, with no success.

Any suggestions on how to go about solving this would be very much appreciated.

Thanks!

---

