---
title: "Help with xorg.conf please?"
date: 2008-08-31
forum: Hardware
---

### Post by mercules2178 on 2008-08-31
I have trolled through the forums trying several different solutions to my monitor problem. I found someone who has very similar situation and hardware. The only difference is I have a 8 series card. He put this info into his xorg.conf and I would like to do the same so that I can get my monitor to work with Nvidia. 
I am going to reinstall Ubuntu and update it. I have used Envy, the restricted, and direct download method to install the drivers and had the same result. The xorg is not being configured correctly. I am going to use the restricted drivers and install nvidia settings. I can not reboot at this point because I will not be able to boot back into my computer unless I do a repair. I would like to know where and how to include this information? 

I would rather use Ubuntu than OpenSuse. I have my hardware working in opensuse but I do not like the feel of the OS.

If anyone could help me I would greatly appreciate it.

[http://ubuntuforums.org/showthread.php?t=846207&highlight=dell+e207wfp](http://ubuntuforums.org/showthread.php?t=846207&highlight=dell+e207wfp)

---

### Post by mercules2178 on 2008-08-31
I have now installed and updated. I restarted and installed the restricted drivers.

I could use the help with the xorg.conf file please?

---

### Post by mercules2178 on 2008-08-31
At this point I entered the info that this person provided and now I am at a resolution of 800x600@73. I could please use some help?

---

### Post by mercules2178 on 2008-08-31
section "Device"
        Identifier     "Configured Video Device"
        Driver         "nvidia"
        Option         "NoLogo"          "True"
        Option         "DynamicTwinView" "False"
EndSection

Section "Monitor"
        Identifier     "Configured Monitor"
        Modeline "1680x1050@57" 146.25 1680 1712 2264 2296 1050 1071 1081 1103 +hsync +vsync
EndSection

Section "Screen"
        Identifier     "Default Screen"
        Monitor        "Configured Monitor"
        Device         "Configured Video Device"
        Defaultdepth   24
        Mode           "1680x1050_57"
EndSection

---

### Post by mercules2178 on 2008-08-31
After running nvida xconfig:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
    Modeline "1680x1050@57" 146.25 1680 1712 2264 2296 1050 1071 1081 1103 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "DynamicTwinView" "False"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Mode       "1680x1050_57
    EndSubSection
EndSection

I now have a resolution of 800x600@73. 
Any Ideas from anyone?

---

### Post by IntuitiveNipple on 2008-08-31
Use System > Administration > System Log. If, in the left side-bar it doesn't list under "/var/log" "Xorg.0.log" then do File > Open..., navigate to the directory /var/log/ and open the file Xorg.0.log.

This is the file the the X window system creates each time it starts. Each entry is prefixed by a tag in brackets, such as 

(II) which means 'information'
(WW) which means 'Warning'
(EE) which means 'Error'.

First, look for any obvious problems by scanning for lines beginning (WW) or (EE).

One or two (WW) can occur without a problem, but there should be no (EE).

Also, read the entire log from the start to get a sense of what it is doing and focus particularly on the lines that mention display resolutions.

You may find a clue that leads to a solution from that.

---

### Post by pietjanjaap on 2008-08-31
Wenn you run nvida xconfig it will change evething.

What if you change it bij hand and then restart ubuntu?



What happens if you boot to the recovery mode, then fix x server, then reboot, then install with envy the video driver?

---

### Post by mercules2178 on 2008-08-31
I have two lines that have (ww)

The directory "/user/share/fonts/X11/cyrillic" does not exist.

The next few lines shows that it corrected the path

The next one:

****INVALID MEM ALLOCATION**** b: 0xde000000 e: 0xde000000 correcting

I believe this pertains to my video considering everything after it deals with my monitor. Near the end of the file it shows that it says that the width too large for virtual size and then chooses the 800x600@73.

not sure what to do now!

---

### Post by mercules2178 on 2008-08-31
current xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "NVIDIA GeForce 8 Series"
        Busid           "PCI:5:0:0"
        Driver          "nvidia"
        Screen  0
        Vendorname      "NVIDIA"
        Option          "NoLogo"        "True"
        Option          "DynamicTwinView" "False"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Dell"
        Modelname       "Dell E207WFP"
        Horizsync       30.0-83.0
        Vertrefresh     56.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
   modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsy$
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync$
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsy$
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync$
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +v$
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsyn$
   modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsyn$
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync$
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync$
  modeline  "1680x1050@60" 146.25 1712 2264 2296 1050 1071 1081 1103 +hsync +vs$
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync$
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1792    1344
                Modes           "1680x1050@60"  "1400x1050@60"  "1400x1050@75" $
        EndSubSection

---

### Post by IntuitiveNipple on 2008-08-31
> **mercules2178 said:**
> 
The next one:

****INVALID MEM ALLOCATION**** b: 0xde000000 e: 0xde000000 correcting

I believe this pertains to my video considering everything after it deals with my monitor. Near the end of the file it shows that it says that the width too large for virtual size and then chooses the 800x600@73.

not sure what to do now!
Can you attach that log-file here so we can take a look? You'll probably need to compress it first, so do:
```

cd ~
cp /var/log/Xorg.0.log .
gzip Xorg.0.log
ls *.gz

 Xorg.0.log.gz

```
Now that file is compressed you can attach it to a post.

---

### Post by mercules2178 on 2008-08-31
here it is

I want to thank you for helping!!!

---

### Post by IntuitiveNipple on 2008-08-31
The problem is this:
```

(II) VESA: driver for VESA chipsets: vesa

```
Your system is not using the nvidia driver, it is using the default VESA (Video Electronics Standards Association) driver. That driver is used as the lowest-common-denominator when other drivers aren't installed or working.
Ubuntu has changed how it deals with bad xorg.conf configurations. In the past it would refuse to start the x-server, but now it quietly falls-back to a default configuration to at least get the xserver started. The problem is, you the user often don't realise it has ignored the xorg.conf you thought it was using!

I suspect what you need to do is reconfigure the xserver, but lets check you've got the nvidia proprietary driver installed. Show us the output of this command:
```

dpkg-query -l 'nvidia*'

```

If you see something similar to this:
```

ii  nvidia-glx-new      169.12+2.6.24.14-21 NVIDIA binary XFree86 4.x/X.Org 'new' driver

```
then you can try reconfiguring the xserver:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
Try restarting the X server after that (log-out, log-in). After log-in check the /var/log/Xorg.0.log again and see if it is still using "VESA". If it is, there *should* be a back-up Xorg.0.log that was written when the system tried and failed to start the nvidia driver. We need to see that, so look in /var/log/ for the most recently timed file prior to the current Xorg.0.log:
```

ls -l /var/log/Xorg*

```
Identify the file, examine the contents to be sure it does refer to the nvidia driver and shows some kind of failure towards the end, then do the copy-gzip-attach-post on that file so we can look at it.

---

### Post by mercules2178 on 2008-08-31
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  nvidia-glx     <none>         (no description available)
un  nvidia-glx-leg <none>         (no description available)
ii  nvidia-glx-new 169.12+2.6.24. NVIDIA binary XFree86 4.x/X.Org 'new' driver
un  nvidia-glx-src <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
ii  nvidia-kernel- 20051028+1ubun NVIDIA binary kernel module common files
un  nvidia-new-ker <none>         (no description available)
ii  nvidia-setting 1.0+20080304-0 Tool of configuring the NVIDIA graphics driv
un  nvidia-xconfig <none>         (no description available)

---

### Post by IntuitiveNipple on 2008-08-31
That shows the nvidia driver is installed, so try the dpkg-reconfigure and then lets see what the log shows.

---

### Post by mercules2178 on 2008-08-31
This is what I get
 sudo dpkg-reconfigure
/usr/sbin/dpkg-reconfigure: please specify a package to reconfigure

---

### Post by IntuitiveNipple on 2008-08-31
> **mercules2178 said:**
> This is what I get
 sudo dpkg-reconfigure
/usr/sbin/dpkg-reconfigure: please specify a package to reconfigure
That's as a result of doing:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
?

---

### Post by mercules2178 on 2008-08-31
This is the other log file:

---

### Post by IntuitiveNipple on 2008-08-31
Okay, that last log-file gives me concerns since one of the first things it reports is:
```

(--) using VT number 9

```
All Ubuntu systems are configured to use VT 7 (Virtual Terminal) so how has yours changed? That leads me to wondering what else has been changed from a standard installation that is now interfering or affecting attempts to return it to working order.

The next thing that concerns me is that the driver being loaded in the Xorg.9.log is *not* the "nvidia" proprietary driver (from nvidia-glx-new) but the standard xorg "nv" open-source driver:
```

(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.1.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0

```
If the "nvidia" driver were being loaded you'd see:
```

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver

```
I think you need to consider all the things you were trying up to this point and try to unpick them since I strongly suspect one or more of them is affecting your attempts to get the correct driver working.

It might be worth removing and reinstalling the nvidia proprietary drivers just to be sure settings and files are as they should be. To do that you should log-out of Gnome/X windows, press Ctl+Alt+F1 to get to console terminal 1, log-in, then stop Gnome, uninstall and reinstall the nvidia driver:
```

sudo /etc/init.d/gdm stop
sudo apt-get --purge remove nvidia-glx-new
sudo apt-get install nvidia-glx-new
sudo /etc/init.d/gdm start

```
Now log-in and see if things are better.

---

### Post by mercules2178 on 2008-08-31
It apears to be the same.

---

