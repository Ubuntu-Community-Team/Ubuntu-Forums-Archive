---
title: "Screen doesn't fit monitor Ubuntu 14.04"
date: 2014-12-03
forum: Hardware
---

### Post by nverbryck on 2014-12-03
Hello, somewhat of a Linux n00b here, I've been checking out various distros lately to replace Windows with, but I have run into a problem with both Ubuntu 14.04 and 14.10 and all variants I've tried.  I have been using a 27 inch Olevia LCD HDTV as my monitor for several years via VGA cable, the native resolution is 1366 x 768 and my graphics card is an Nvidia 9800 GTX +.  

I have installed Nvidia driver 331.38, but when I set my resolution to 1366 x 768 the screen does not align with the TV, there is a gap on the left and right and the bottom of the screen scrolls off the monitor.  Right now I am basically stuck running 1024 x 768 which means about 1/3 of the screen is not being used.  Is there any way to fix this?  I am no expert at the command line.  I am able to set the monitor to the proper resolution just fine in Windows.  I would prefer to use Ubuntu than Windows though, and don't want to buy a new monitor.  Any help is much appreciated, thanks in advance.

---

### Post by carl4926 on 2014-12-03
The resolution you quote for the screen sounds incorrect for a 27" screen. Regardless, the system should should auto detect without any fiddling.
When you ran Ubuntu live, did it fit the screen?

---

### Post by nverbryck on 2014-12-03
No, the live CD ran at 1024 x 768 by default and if I tried to change it same result with it being off.

---

### Post by carl4926 on 2014-12-03
Did you try with nomodest?

---

### Post by ajgreeny on 2014-12-03
Ina terminal run command **xrandr** to see if the resolution you want is listed.

Does the information you have for your Olevia LCD HDTV tell you what the resolution of that really is, or is that where you got the 1366x768 figure from?  It does sound a bit strange for that size screen.

---

### Post by carlwsnyder on 2014-12-03
The nVidia driver you are using seems to not be the proper driver for your nVidia GeForce 9800 GTX+ system.  Did you install by installing the nvidia-current driver or did you manually choose the driver?  According to the listing on Google, you should be using the 340.xx series driver [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)  You may want to try installing the proper driver for your system.  For those who are questioning the resolution figure of 1366x768, that is the normal resolution of a 720P display.

---

### Post by nverbryck on 2014-12-03
Thank you for the replies.  The TV is several years old and is 720P, hence the resolution of 1366x768.  I ran xrandr and the highest resolution listed was 1360x768 with 60.0 and 59.8 listed as refresh rates.  How would I go about installing the 340.xx series driver?  Using the additional drivers tool on Ubuntu 14.10 fully updated the only ones listed were 331.38 and 304.117 as well as the nouveau driver, all of which seem to run into the same problem.

---

### Post by carlwsnyder on 2014-12-03
The very latest nVidia drivers are not available yet from Ubuntu, but are available here: [http://www.nvidia.com/Download/driverResults.aspx/77844/en-us](http://www.nvidia.com/Download/driverResults.aspx/77844/en-us)  Instructions for installation of nVidia's drivers are also available in links from the same page.  Be aware that these are not really production tested and ready yet.

You might find better response simply using the **nouveau** driver and setting **xrandr** to the 1360x768@60Hz setting, if **xrandr** reports VGA-0, VGA-1, LVDS-0, LVDS-1, etc. or any other connected display name other than just **default**.  If **xrandr** or any other driver reports connection to **default** and/or cannot read **gamma** setting for the monitor, the only thing I have found to work is to switch drivers.

---

### Post by kostkon on 2014-12-03
Have you tried pressing the auto-setup button or to manually align the image (if there is such an option on your TV)?

---

### Post by carlwsnyder on 2014-12-04
You can also check on other nVidia drivers from the repositories for ones compatible with your GPU.  For example, I am running the 173.xx drivers for my Xubuntu 14.04 installation because they worked with fewer lags than the recommended 304.xx drivers.

---

