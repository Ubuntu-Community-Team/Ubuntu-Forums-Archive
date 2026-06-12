---
title: "Monitor resolution changing randomly, xrandr failed"
date: 2021-10-21
forum: Hardware
---

### Post by leodp on 2021-10-21
Hi all,

new system, new problems.
I have a MSI MAG B550M MORTAR WIFI with an AMD Ryzen 7 5700G CPU, coming with integrated graphics and 2 monitor outputs: a Display port and an HDMI. OS: Linux Mint, 2021.10, installed wiping the previous linux installation.
Normally I have 2 monitors connected: on Display Port a display with resolution 2560x1440, on HDMI a 4k display usually with resolution reduced down to HD. Sometimes this second monitor is disconnected.

No matter what I do, when I switch the system on the resolution on Display Port is randomly correct (2560x1440) or at a lower resolution (for ex. 1440x900).

In case the system boots with a lower resolution, the 2560x1440 is not available when I check with xrandr.

If I add it (cvt, newode, addmode ...) then it is not accepted and xrands returns the error Configure crtc X failed.

The same thing (random resolution at boot, not possible to increase the resolution) happens if I have only one monitor connected at boot, and also if the monitor is connected to the HDMI output instead of the Display Port.

But: when I'm on a low resolution if I switch the connected monitor to the second graphic output then I have on this second port the requested high resolution--> only one graphical output at a time has limited resolution.

I have tried with a startup xrandr script which switches off the monitors and then turns on only one at 2560x1440, but I couldn't get it to solve the issue.

I even changed the setups on the BIOS related to the onboard graphics. It didn't help either.

My idea is that the Ryzen onboard GPU does not have enough resolution to drive both display outputs at the max resolutions available on both, independently on the monitor connected, so it sets one port (which may be different at each boot) correctly, hand has not enough canvas available for the second port to allow the resolution I ask for.

Does it make any sense?
Is there anything I can do to stabilize the system?

Thanks,
leodp


:popcorn:
**UPDATE: Probably it's not related to Linux/XORG & co. I found a probable reason and a quick and dirty solution. See post #8:**

[HTML]https://ubuntuforums.org/showthread.php?t=2468202&p=14075241#post14075241[/HTML]

---

### Post by TheFu on 2021-10-21
**xrandr** is for X11 only, not Wayland.  Before you login, be certain to choose xorg.
I don't know how Wayland works.

Also, I don't have an igp on my Ryzen now, but should by the end of the day (building new system). I should know more then.

---

### Post by leodp on 2021-10-21
MY error, sorry: I'm using Ubuntu MATE, not MINT, which has Xorg. --> xrandr is working, but with the issues I described above

---

### Post by leodp on 2021-10-31
I saw something fishy in /var/log/Xorg.0.log:

```
[    76.587] (II) AMDGPU(0): EDID vendor "AOC", prod id 12921
[    76.587] (II) AMDGPU(0): Using hsync ranges from config file
[    76.587] (II) AMDGPU(0): Using vrefresh ranges from config file
[    76.587] (II) AMDGPU(0): Printing DDC gathered Modelines:
[    76.587] (II) AMDGPU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync +vsync (88.8 kHz eP)
[    76.587] (II) AMDGPU(0): Modeline "2560x1440"x0.0  296.00  2560 2568 2600 2666  1440 1443 1448 1481 +hsync -vsync (111.0 kHz e)
[    76.587] (II) AMDGPU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    76.587] (II) AMDGPU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
......
[    76.587] (II) AMDGPU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    81.386] (II) AMDGPU(0): Allocate new frame buffer 2560x1440
[    81.387] (II) AMDGPU(0):  => pitch 10240 bytes
[    81.425] (EE) AMDGPU(0): failed to set mode: Cannot allocate memory
[    81.524] (EE) AMDGPU(0): drmmode_do_crtc_dpms cannot get last vblank counter
[    81.525] (II) AMDGPU(0): Allocate new frame buffer 1440x900
[    81.525] (II) AMDGPU(0):  => pitch 6144 bytes
[    81.703] (II) AMDGPU(0): EDID vendor "AOC", prod id 12921
[    81.703] (II) AMDGPU(0): Using hsync ranges from config file
[    81.703] (II) AMDGPU(0): Using vrefresh ranges from config file

```

I guess the **failed to set mode: Cannot allocate memory** means there are issues in the kernel, right?
In BIOS I assigned 4GB to the onboard graphics, there should be enough space.

If I unplug/plug/unplug a monitor in the HDMI port then most of the times I can scale up resolution also in the DP port.
Xorg.0.log says then:

```
[ 23453.165] (--) AMDGPU(0): HDMI max TMDS frequency 340000KHz
[ 23453.167] (II) AMDGPU(0): EDID vendor "AOC", prod id 12921
[ 23453.167] (II) AMDGPU(0): Using hsync ranges from config file
[ 23453.167] (II) AMDGPU(0): Using vrefresh ranges from config file
[ 23453.167] (II) AMDGPU(0): Printing DDC gathered Modelines:
[ 23453.167] (II) AMDGPU(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync +vsync (88.8 kHz eP)
[ 23453.167] (II) AMDGPU(0): Modeline "2560x1440"x0.0  296.00  2560 2568 2600 2666  1440 1443 1448 1481 +hsync -vsync (111.0 kHz e)
[ 23453.167] (II) AMDGPU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[ 23453.167] (II) AMDGPU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[ 23453.167] (II) AMDGPU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[ 23453.167] (II) AMDGPU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[ 23453.167] (II) AMDGPU(0): Modeline "1280x1440"x0.0  156.00  1280 1376 1512 1744  1440 1443 1453 1493 -hsync +vsync (89.4 kHz e)
[ 23453.167] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)

```

---

### Post by TheFu on 2021-11-01
I would snag those modelines and put them into a custom xorg.conf file.  This way, they don't need to be "discovered", since that appears to be the issue.
Here's my custom xorg for nvidia [https://paste.ubuntu.com/p/GCDd9HwVSh/](https://paste.ubuntu.com/p/GCDd9HwVSh/) ... DO NOT JUST COPY IT!!!!!  That will be very bad.  Use it as an example only.
It will only be pasted for 30 days at that link.

The filename I chose to use was: /etc/X11/xorg.conf.d/20-nvidia.conf
I think only files that end in .conf will be used automatically.  You don't need the sections that don't need to be customized.  You'll want the 
**Section "Monitor"**.

On my new 5600G, I've set the video RAM to be 1G only. I know that most of my "desktop" VMs only use 64MB of RAM and that's at 1920x1200     59.95

---

### Post by leodp on 2021-11-06
Thanks TheFu,
I tried your way.
And for sure I would have gotten to the solution...
some years ago. But the Xorg --configure generated xorg.conf is too complex for me to begin with: the connections have a busID which I'm not able to map to the correct HDMI/Video port, the online guides are too outdated, xrandr uses naming conventions which do not fit with xorg.conf and on and on.

I ended up installing the new kernel 5.15, which as updated drivers for randr and which works out of the box, I followed the instructions here [https://ubuntuhandbook.org/index.php/2021/11/linux-kernel-5-15-out/]("https://ubuntuhandbook.org/index.php/2021/11/linux-kernel-5-15-out/"), which are updated for Ubuntu 21.10:

```

wget -c https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15/amd64/linux-headers-5.15.0-051500_5.15.0-051500.202110312130_all.deb

wget -c https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15/amd64/linux-headers-5.15.0-051500-generic_5.15.0-051500.202110312130_amd64.deb

wget -c https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15/amd64/linux-image-unsigned-5.15.0-051500-generic_5.15.0-051500.202110312130_amd64.deb

wget -c https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15/amd64/linux-modules-5.15.0-051500-generic_5.15.0-051500.202110312130_amd64.deb

sudo dpkg -i *.deb

```

Thanks to all,
leodp

---

### Post by TheFu on 2021-11-06
There is a tool called "mainline" which helps manage using unsupported kernels.
I'm running 5.11.20-051120-generic on an 18.04 box to get Ryzen 5xxxG drivers, for example.  I'm not ready for newer OS versions, but the newer kernel provides AMD drivers.

**mainline** lets me stay on "stable" kernels, but keep up with any new versions available.  
```
----------------------------------------------------------------------
Found installed: 5.4.0.89.100~18.04.79
Found installed: 5.4.0-89.100~18.04.1
Found installed: 5.11.20-051120.202105120733
Found installed: 5.4.0-87.98~18.04.1
----------------------------------------------------------------------
----------------------------------------------------------------------
Latest update: 5.15.1
```

```
$ mainline --help
mainline 1.0.15
Distribution: Ubuntu 18.04.6 LTS
Architecture: amd64
Running kernel: 5.11.20-051120-generic

mainline 1.0.15 - Ubuntu Mainline Kernel Installer

Syntax: mainline <command> [options]

Commands:
....
```

Guess there are multiple ways to a solution.  Seems 5.10.x or later kernels are needed to get the Ryzen 5xxx igp drivers. I didn't know that in my original post. Sorry. The new kernel got me to a very stable setup:
```
$ uptime 
 16:02:43 up 14 days,  3:13,  
```

---

### Post by leodp on 2022-01-13
Hi,
I have to correct what I wrote above.
The new kernel did not really do the job, the resolution of the screen toggles unpredictably, even if in a first moment it looked ok. Even kernel 5.16, with many improvement for my integrated graphic card is not ok.

What I found out is that if the initial max recognized monitor resolution is not the correct one this is due to a problem in getting the EDID. After a while the PC receives again the correct one and I can set it manually.

A quicker solution: if the initial resolution is wrong I have to switch off and on the monitor. Probably in that way I force the re-acquisition of a correct EDID.
I still do not understand the reason. It may be that the new PC is much quicker than the old one and boots before the monitor is operative, thus having issues in recognizing what is attached to the video card.

Leo

---

