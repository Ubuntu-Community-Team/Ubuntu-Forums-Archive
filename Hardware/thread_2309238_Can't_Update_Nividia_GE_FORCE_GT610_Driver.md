---
title: "Can't Update Nividia GE FORCE GT610 Driver"
date: 2016-01-08
forum: Hardware
---

### Post by AUDIOTEK on 2016-01-08
I'm having issues with installing the driver for a GT610.  I'm running Ubuntu 14.04.4 with an Intel Pentium4 3200Mhz chip. 2.7Gb of RAM

I get this error message after 1 hour of installation

"There was a problem opening the file "/home/,,,/....NVIDIA-Linux86_295.53.run"

The file you opened has some invalid characters..."


What I'm trying to do is run VLC at 1080p with Hardware Acceleration but I don't think VLC sees the GT610, after I save the settings for VLC to use the GT610 the CPU is still at full usage around %97 on both core.  

As far as driver goes it's using the X.org driver 1.15.1 according to HardInfo

---

### Post by Yellow Pasque on 2016-01-09
> here was a problem opening the file "/home/,,,/....NVIDIA-Linux86_295.53.run
I don't think the answer is to mess with the driver, especially trying to install an old, unsupported driver off the Nvidia site which it looks like you're trying to do.

Try this first and see if it helps with CPU usage in VLC:
```
sudo apt-get install vdpau-va-driver
```

If it doesn't help, check the outputs of vdpauinfo and vainfo:
```
sudo apt-get install vdpauinfo vainfo
vdpauinfo
vainfo
```

You may also find this page helpful: [https://wiki.videolan.org/VLC_GPU_Decoding/](https://wiki.videolan.org/VLC_GPU_Decoding/)

---

### Post by AUDIOTEK on 2016-01-09
Thanks for the reply.  So what you are saying is not to use the proprietary driver from Nvidia?

---

### Post by oldfred on 2016-01-09
If you look here you see the latest verions.
       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Depending on vesion of Ubuntu you will not have the most current version of nVidia driver but most current version available in repository will work with that card. Or to get newest version use ppa.

      
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

   # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices
sudo apt-get update && sudo apt-get install nvidia-3xx

---

### Post by Yellow Pasque on 2016-01-09
> **AUDIOTEK said:**
> Thanks for the reply.  So what you are saying is not to use the proprietary driver from Nvidia?

I really don't know how to make my previous post any clearer..

---

### Post by AUDIOTEK on 2016-01-09
I tried [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install vdpau-va-driver 
[/FONT][/COLOR]and it improved the video a lot.  It's almost watchable, there's no pixelation but the picture is very jerky but at least that's an improvement!!!   And same thing both CPUs are fully loaded to %100 each. When I open a small app like System Monitor the video turns into a mosaic!!!

So if I understand this well the problem is not that my system is not able to use the GT-610 since I have video output off the HDMI but the problem is that VLC cannot use the GPU? 
If I go in VLC  PREFERENCES---->INPUTS/CODECS--->HARDWARE ACCELERATED DECODING 
I have 3 options

1-Automatic
2-Video Acceleration (VA) API  which I assume is the integrated graphic card
3-Disable

And that's it.  Where do I actually select the GPU from?

When I go to VLC---->VIDEO--->OUTPUT  it seems that XVideo Output (XBC) works the best!!!!

---

### Post by AUDIOTEK on 2016-01-09
I guess I already had the latest and recommended version

*nvidia-352 is already the newest version.*
*The following packages were automatically installed and are no longer required:*
*  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic*
*  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic*
*Use 'apt-get autoremove' to remove them.*
*0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.*

---

