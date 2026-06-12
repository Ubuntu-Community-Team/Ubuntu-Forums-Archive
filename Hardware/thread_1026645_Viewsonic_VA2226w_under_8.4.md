---
title: "Viewsonic VA2226w under 8.4"
date: 2008-12-31
forum: Hardware
---

### Post by arohanui on 2008-12-31
I've just updated 7.10 to 8.4 and weirdly, my display is having issues. It can't find the drivers for my Viewsonic VA2226w widescreen monitor, which is weird, since it was working just fine before I updated.

And my googlefu is failing me, I can't find the linux drivers for the VA2226w anywhere.

Can anybody help me?

(Apologies for the double post, I wasn't sure whether this belonged in Multimedia or here.)

Thanks

---

### Post by arohanui on 2008-12-31
After updating successfully to 8.10, the system is now no longer running in low graphics mode, but still cannot successfully dectect the driver (and I can't understand where it's gone, since it was all working fine before the OS update).

It's displaying ok, but in the wrong resolution and aspect ratio, so everything is sort of smeared out.  I can't change it to the correct one, since it doesn't list the correct res options against the default display.

I'd be very appreciative of any ideas here.

---

### Post by arohanui on 2008-12-31
Ah ok, whoops.  Trying to find a default resolution at the correct aspect ratio (what *is* 1600x1024?) I chose the wrong one, and now I can't see squat.  I also can't figure out how to get back into safe graphics mode to change the res back to something that I can at least work with.

I'm begging you, help me out here.

---

### Post by arohanui on 2008-12-31
I can neither escape to the GRUB menu (frantic mashing of the escape key and any function key I can think of does nothing), nor switch to a tty once in my garbled Ubuntu session.

What am I going to do???

---

### Post by arohanui on 2009-01-01
I used ctrl-alt-F2 to get to a tty, then
sudo dpkg-reconfigure -phigh xserver-xorg
to reset the X11 to a "safe graphics mode".

I then exited the tty, and ctrl-alt-backspace to restart X11, and voila! 
Safe Graphics Mode.

So now I can see at least, now I just need to figure out how to configure the monitor correctly.

---

### Post by arohanui on 2009-01-01
I used System>Admin>Hardware Drivers to activiate the nvidia proprietory drivers.

I then
sudo vim /etc/X11/xorg.conf
to manually configure my monitor.

I've tried a Monitor section:
```
Identifier  "Configured Monitor"
VendorName  "ViewSonic"
ModelName   "VA2226w"
HorizSync   30.0 - 82.0
VertRefresh 50.0 - 75.0
Option      "DPMS"
```
which are apparently the correct values, but it's not working.

I'm getting the following error:
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernal module:
<snip>
(EE) Screen(s) found but none have a usable configuration.

---

### Post by arohanui on 2009-01-01
I've seen via google some mention of checking /etc/driver_aliases, but I'm not entirely sure what I'm looking for.

[http://www.phoronix.com/scan.php?page=article&item=406&num=1](http://www.phoronix.com/scan.php?page=article&item=406&num=1)

---

### Post by arohanui on 2009-01-10
I'm still having no joy on this. I can only select from a default list of resolutions at System>Preferences>Screen Resolution: 1280x1024, 1024x768, 800x600, or 640x480. I'm currently running 1024x768 (which is at least the correct aspect ratio), but it should be in 1600x1050.

My /etc/X11/xorg.conf file:
```


Section "Monitor"
        Identifier      "Configured Monitor"
        VendorName      "ViewSonic"
        ModelName       "VA2226w"
        HorizSync       30.0 - 82.0
        VertRefresh     50.0 - 75.0
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

Anyone any ideas?

---

### Post by arohanui on 2009-01-11
Haha oops, I was missing a EndSubSection in the above, but I fixed that and still no joy (I no longer get (EE) parsing errors, but instead get the original (EE) Screen(s) found but none have a usable configuration error).

I've also tried reverting to an old (pre-update) xorg.conf file, but the problem persists.

---

### Post by arohanui on 2009-01-11
I came across someone with similar problems ([https://answers.launchpad.net/ubuntu/+source/xorg/+question/44998](https://answers.launchpad.net/ubuntu/+source/xorg/+question/44998)) solving the issue using displayconfig-gtk.  Sadly, I don't seem to be able to install this:
```

~% sudo apt-get install displayconfig-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package displayconfig-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package displayconfig-gtk has no installation candidate

```

Seriously, any ideas at all would be incredibly welcome.

---

### Post by amadeujr on 2009-10-18
In my case, I see in my /var/log/Xorg.0.log that my Nvidia proprietary driver reports the VideoRAM size as 512MB, but I have a 128MB shared memory in my Geforce Go 6150. I really don't know the why, but when I tried:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
    VideoRam       131072  
EndSection

And.. magically it works! I get the 1600x1050 resolution again! Before this configuration I just got 1360x768 and 1024x768 for my 22" LCD Monitor.

My horiz/vert refresh rate are:
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

I hope this help you.

---

