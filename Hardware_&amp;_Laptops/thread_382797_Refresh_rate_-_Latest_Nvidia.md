---
title: "Refresh rate - Latest Nvidia"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by Sale on 2007-03-12
Hi

Does anyone know how to set the monitor refresh rate using the latest nvidia driver and Nvidia GeForce 7600 GS card?

I'm using 1280x960 resolution (used to run at 85Hz with ATI and an Nvida card i used before ATI) and Sustem->Preferences->Screen Resolution says that the refresh rate is 109Hz, which is impossible on my old 17" Samsung, while the Applications -> System -> "Nvidia X Server settings" reports thet the monitor is running at 60Hz. The latter feels closer to the truth..

Adding Modleines to the xorg.coonf doesn't work. It looks like I'd need to ad a new MetaMode to "Nvidia X Server settings" but I have no idea how to do that.

TIA

Sale

---

### Post by taurus on 2007-03-12
Did you also add the horizontal and vertical refreshing rates for your monitor in /etc/X11/xorg.conf?

---

### Post by Sale on 2007-03-12
Yes, I did add the h/v frequencies...Nothing I do in xorg.conf seems to make no difference.

And I have another problem. I'm not sure if it's related to the first one or not.

My X server just doesn't start after a reboot. I've tried reinstalling the driver several times. I can use startx or /etc/init.d/gdm start commands right after I install the driver, but after a reboot the the x doesn't start. The log says thet I xave the "x module" 1.0-9755 (which is how it should be, that is the laatest driver version) but I seem to have 1.0-7174 "Nvidia kernel module" which I know nothing about. Nor do I know how to install the propper "Nvidia kernel module"

---

### Post by John.Michael.Kane on 2007-03-12
The resolution issue might be fixed using the second post.. [**Adjust xorg resolution**]("http://ubuntuforums.org/showthread.php?t=289269&highlight=modeline") note: you may need your CRT/LCD manual for some of the specs.

For the other issue you may have to reset your xorg.conf file.

**Run:**
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Sale on 2007-03-12
Thanks SD-Plissken but 

```
dpkg-reconfigure -phigh xserver-xorg

```

didn't help :(

It looks like Ubuntu simply doesn't reckognize my Video card ??

BTW, I already did all as you wrote in the other thread you pointed me to, but no use.
Still, I guess we can leave the refresh rate issue alone for now...

And yes..here is my video card:
[http://www.msi.com.tw/program/products/vga/vga/pro_vga_detail.php?UID=754](http://www.msi.com.tw/program/products/vga/vga/pro_vga_detail.php?UID=754)

---

### Post by mannheim on 2007-03-14
> **Sale said:**
> Sustem->Preferences->Screen Resolution says that the refresh rate is 109Hz, which is impossible on my old 17" Samsung, while the Applications -> System -> "Nvidia X Server settings" reports thet the monitor is running at 60Hz. The latter feels closer to the truth..


I can answer this part of the question. In the ReadMe file for the nvidia binary driver, it mentions this as a known issue: apps like the gnome screen-resolution control panel report the refresh rate incorrectly, for reasons which are explained in the readme (but which are beyond my comprehension). You have to go by what the Nvidia Settings control panel says.

---

### Post by NikoC on 2007-03-14
I have the same issue: nvidia-settings gives me the right refresh rate of 60 Hz while gnome doesn't (50 Hz). Wouldn't worry about it too much though.

---

### Post by Sale on 2007-03-16
I've managed to set up the refresh rate and the resolution that i wanted (1280x960_85) using "nv" driver, but without 3d acceleration.

Another thing I've noticed: After I instal the nvidia driver, and reboot, X crashes with the report about "module missmatch". It says that I have 1.0-9755 X module (this is consistent with the driver version) and 1.0-7174 nvidia kernel module.The only kernel I have installed is 2.6.17-11-386. What can be done about this?

---

### Post by Sale on 2007-03-17
OK, now...I've **almost** solved both problems :)

The issue of the X Server crashing after a reboot when nvidia proprietary driver is installed is resolved by compiling and installing the latest linux kernel from  [http://www.kernel.org/](http://www.kernel.org/) , or, at least, the one newer than Ubuntu 2.6.17-11-386 kernel.

To do that, you should follow either of these two HOWTOs:
[http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation)
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

As for the refresh rate problem, it looks like nvidia mode validation system doesn't reckognise 1280x960@85 as a valid mode for my monitor. This is odd, becose nv driver does, as well as the Windows nvidia driver. So, I was able to go as far as 75Hz by adding modeline for 75Hz to "Section: Monitor" and "1280x960_75 +0+0;" to the "Option: metamodes" line in xorg.conf.  Doing this makes the "Modes" line of the "Section: Screen" in xorg.conf irrelevant.

So...I hope this helps someone  :)

---

