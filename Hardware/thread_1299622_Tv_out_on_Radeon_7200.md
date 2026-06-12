---
title: "Tv out on Radeon 7200"
date: 2009-10-24
forum: Hardware
---

### Post by CoreyJKelly on 2009-10-24
Hi All,

I've been scouring the internet for days trying to sort this out, with no luck. Hoping someone here has some insight. 
I'm running Jaunty on a relatively old system which has an ATI Radeon 7200 video card. The computer will be used exclusively with a TV, and I can't get seem to get the TV output to work. The entire boot process shows up on the TV, but as soon as X starts, it goes black (there's still a signal, it's just blank.) It's a completely fresh install, and I've tried a bunch of different things, from playing around with the xorg.conf file, to changing drivers, and found a promising solution here:
[http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)
Sadly, these instructions produced no results. While trying to build the driver, I'm running into multiple errors. Since the instructions were written for Edgy, I wasn't surprised. 
I'm not a complete Linux newbie, and I'm pretty comfortable with the terminal, but this is baffling me.

I hope someone out there has dealt with a similar problem, and might be able to help me out a bit!

---

### Post by JBAlaska on 2009-10-24
I'ts been a while since I had to deal with ati drivers, but please post your ```
/etc/X11/xorg.conf
``` file and lets have a look

Edit: I might not be on-line much longer, so...It may simply be a refresh rate problem and as 9.04 will self config, just try renaming your xorg.conf to xorg.conf.bak and restart x or reboot. If that does not work post your xorg.conf contents as above and the output of ```
$ lspci -nn | grep VGA
``` and ```
$ glxinfo |grep vendor
``` and someone I'm sure will carry on, Good luck.

---

### Post by CoreyJKelly on 2009-10-24
Well like I said, it was a fresh install, so when I started this whole mess, the xorg.conf was blank. It is current set up exactly as suggested in the link I posted:

```
Section "Device" 
    Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]" 
    Driver "ati" 
    BusID "PCI:1:0:0" 
    Option "TVOutput" "NTSC"
EndSection

Section "Monitor"
    Identifier "SyncMaster"
    HorizSync 30 - 50
    VertRefresh 60 - 60
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]" 
    Monitor "SyncMaster" 
    DefaultDepth 24 
    SubSection "Display" 
        Depth 24 
        Modes "800x600" 
    EndSubSection 
EndSection
```

---

### Post by JBAlaska on 2009-10-24
Try this;
```
Section "Device" 
    Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]" 
    Driver "radeon" 
    BusID "PCI:1:0:0" 
    Option "TVOutput" "NTSC"
    Option "ForceTVOut" "ON"

EndSection
```

Also make sure your BusID is correct with lspci (lspci reports hexadecimal numbers, xorg.conf needs decimal)

Also make sure Make sure libgl1-mesa-glx and libgl1-mesa-dri are properly installed:

```
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```

I have to get some sleep (have a early day), good luck!

---

### Post by CoreyJKelly on 2009-10-24
I've tried the radeon driver as well, and reinstalled the packages you recommended. No luck! As for the BusID, I checked lpsci again, and the value listed was "00:1.0". I tried changing the value in xorg.conf to PCI:0:1:0, and now I can't even get an image on my monitor when X loads. Not sure how to fix that... I know I can get a command line up in grub, but I'm not sure if I can edit the xorg.conf file from there. Ideas?

---

### Post by CoreyJKelly on 2011-01-23
Sorry to resurrect this thread, but the only reason it died off is because I gave up. I've come back to the problem now, and all of the above is still true, except that I'm now running 10.10. 

This is mostly frustrating because I know there's a signal being output, but it's blank. I've tried endless permutations of settings in xorg.conf with no success. The TV displays the entire boot process, but as soon as X starts, the screen goes black. I'm using VNC to access the box, and it doesn't seem to be detecting the TV (nothing listed in Preferences > Monitors.)

I'm coming really close to just buying a VGA->composite converter, but it would be great if I didn't have to.

---

### Post by dandnsmith on 2011-01-23
Have you checked the capabilities of the radeon and other candidate drivers for U 10.10
I've the feeling that your card isn't supported in the latest releases for the radeon driver.
The default for some radeon cards which I've tried with 10.04 was vesa - which was what set me hunting.
I don't have details of the page to check, but it should be reachable from the x.org site

---

### Post by CoreyJKelly on 2011-01-23
My card most definitely isn't supported in the latest drivers. The link in my first post outlines a patching process which is meant to fix this, but only guarantees it will work with Edgy. The patch got me from no signal at all to a blank one, so it was a step in the right direction.
I played around with vesa a bit when I last explored this problem, with no success.

---

