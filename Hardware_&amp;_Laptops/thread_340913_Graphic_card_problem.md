---
title: "Graphic card problem"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by Jyrenth on 2007-01-17
I'll start off by saying I can't seem to get my graphics card to work with Ubuntu on my laptop.  I'm running 6.06LTS, the kernel is 2-6.15-27-386.  The laptop is a Dell XPS M170, the graphics card is a GeForce Go 7800 GTX.

Linux doesn't seem to realize I have a graphics card at all.  It's not listed in the device manager, and any 3D games I tried to run would be way slower than my computer's capabilities.  I installed the correct linux-restricted-modules for my kernel and installed nvidia-glx as per this tutorial: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
but when I run this command:
sudo nvidia-glx-config enable
it gives an error telling me to do this:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
so I do, run the command, and when I restart the computer it crashes telling me it can't load the GUI so I have to go back to my backup xorg.conf.

What am I doing wrong?

---

### Post by RandomJoe on 2007-01-17
I have never been able to use the "nvidia-glx-config enable" script - it always gives me that error as well, even on a brand-new fresh install.

I just manually edit the xorg.conf file myself after running nvidia-glx-config - open it up, and scroll down until you find a section like:
```
Section "Device"
        Identifier      "card1fp1"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection
```
I changed the Identifier line as well since I have multiple screens, but the default will describe your card.  Just change the driver from "nv" to "nvidia" then restart X.

The md5sum line changes the expected md5sum to match the current file, so that the nvidia-glx-config command will work.  In theory that ought to do just the above, but perhaps it's editing the wrong line somewhere because the file isn't what it expects...?  (Again, I never tried this, just edited the file manually since it's a trivial change.)

---

