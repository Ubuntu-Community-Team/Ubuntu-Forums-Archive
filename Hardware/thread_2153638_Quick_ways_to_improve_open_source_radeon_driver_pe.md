---
title: "Quick ways to improve open source radeon driver performance"
date: 2013-06-11
forum: Hardware
---

### Post by maestrobwh1 on 2013-06-11
Using an Asus EEEPC 1201T which pretty much works out of the box wth 13.04.  Had been using ubuntu 12.04 with the fglrx driver but wanted to refresh my machine with 13.04. 

Graphics performance sucks out of the box **so I post this to help others free themselves from the fglrx situation and have a nicely running machine with the open source driver, radeon**:

This is my card: VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780M [**Mobility Radeon HD 3200**]

So fglrx no longer supports this card past 12.04 anyway so it really isn't even a choice for me.  I tried older versionsof fglrx that I knew worked but they would not compile with the kernel 3.8.0-23

So I was stuck with the radeon driver which made my machine run really hot (60 to 70 Celcius) compared to the fglrx driver (always hovered between 50-58 C).  And graphics were terribly sluggish on top of that doing normal tasks (web browsing). Not okay for this middle of the road card (as in, it is not high end, but not a clunker either).

After web searching, **these two things dramatically increased performance while allowing the machine to run cooler**: I can barely hear the fan now.

Firstly:

```
sudo nano /etc/pm/power.d/radeon_power_profile
```

paste this in

```
#!/bin/sh
 
echo profile > /sys/class/drm/card0/device/power_method
echo auto > /sys/class/drm/card0/device/power_profile
 
exit 0
```

make it executable

```
sudo chmod +x  /etc/pm/power.d/radeon_power_profile
```

I also put both "echo" commands into /etc/rc.local, but that is perhaps redundant.

Secondly (I compiled this from a list of options I found for the radeon card in xorg.conf):

```
sudo nano /etc/X11/xorg.conf
```

paste this in

```
Section "Device"
        Identifier      "ATI"
        Driver          "radeon"
        # acceleration
        Option          "AccelMethod"   "EXA"
        Option          "ColorTiling"   "on"
        Option          "AGPMode" "4"
        Option          "EnablePageFlip" "on"
        Option          "RenderAccel" "on"
        Option          "AGPFastWrite" "yes"
        # enable (partial) PowerPlay features
        Option          "DynamicClocks" "on"
EndSection
```

Before you reboot, read my caution below:

Namely, EnablePageFlip, AGPFastWrite and AGPMode are not enabled by default because on some cards, they presumably *can cause instability or prevent X from starting*: my machine seems even more stable.  We've been told why these options are not enabled by default, so please either know how to get to a terminal if X refuses to start, and have a CD or bootable usb drive so you can comment things out if need be to get yourself back to a working X.  The latter can be set to 8 on my card; if you are advanced and know how to work around X not starting like some of us, try it.  The defualt is 1, so that is why the Radeon driver might seem to be really sluggish by default.  *Safe:*  EXA is supposed to be the default setting, and ColorTiling is supposed to be ON by default, but all reports seem to say that putting these in will ensure optimal performance.  "DynamicClocks" is also "newer" and is supposed to dial back the card, hence cause cooler operation and better battery life, when heavy graphics applications are not running.  I am thinking the first tweak ensures "medium" performance but they both together seem to give me the performance I want on my sub-notebook: resonable performance with longer battery life.

My temperature is currently 53 C, and performance seems, in a non quantitative assessment, to be at least the same as Ubuntu 12.04 with fglrx.  I actually think it is running cooler and my battery is still showing 2 hours of life, and I have been using it for 1.  I never got more than 2 hours total before.  

Now you can Reboot.  Good luck. If X doesn't start, find yourself in "safe boot," choose root, and comment out the 3 things I mentioned as potential stability issues and go from there.

I have found this to be sometimes the case: You might have to issue a 

```
mount -o remount,rw /
``` 

IF / goes into read only mode when going into root mode.

---

