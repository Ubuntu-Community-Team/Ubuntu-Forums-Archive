---
title: "Ubuntu 10.04 Not Detecting Monitor Correctly"
date: 2010-07-05
forum: Hardware
---

### Post by tigerglebe on 2010-07-05
I've got Ubuntu 10.04 LTS running on an nVidia Geforce 4 MX 420 AGP connected to a Westinghouse LCM-20v5.  This monitor is able to go to 1400 x 1050 under Windows XP.  Under the default install drivers of Ubuntu it's limited to 1024x748 while the nVidia drivers under restricted hardware refuse to budge above 640x480. 

I would like some help to fix this please.

---

### Post by SergeiFranco on 2010-07-05
After I installed updates (which included nvidia drivers I believe) I am also stuck at 640x480.

```
(**) Jul 05 21:49:21 NVIDIA(0): Enabling RENDER acceleration
(II) Jul 05 21:49:21 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jul 05 21:49:21 NVIDIA(0):     enabled.
(II) Jul 05 21:49:22 NVIDIA(GPU-0): Display (ViewSonic VX2235wm (DFP-0)) supports NVIDIA 3D Vision
(II) Jul 05 21:49:22 NVIDIA(GPU-0):     stereo.
(II) Jul 05 21:49:22 NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:1:0:0 (GPU-0)
(--) Jul 05 21:49:22 NVIDIA(0): Memory: 524288 kBytes
(--) Jul 05 21:49:22 NVIDIA(0): VideoBIOS: 62.92.12.00.04
(II) Jul 05 21:49:22 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jul 05 21:49:22 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jul 05 21:49:22 NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:1:0:0:
(--) Jul 05 21:49:22 NVIDIA(0):     ViewSonic VX2235wm (DFP-0)
(--) Jul 05 21:49:22 NVIDIA(0): ViewSonic VX2235wm (DFP-0): 330.0 MHz maximum pixel clock
(--) Jul 05 21:49:22 NVIDIA(0): ViewSonic VX2235wm (DFP-0): Internal Dual Link TMDS
(II) Jul 05 21:49:22 NVIDIA(0): Assigned Display Device: DFP-0
(WW) Jul 05 21:49:22 NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) Jul 05 21:49:22 NVIDIA(0): 
(WW) Jul 05 21:49:22 NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) Jul 05 21:49:22 NVIDIA(0):     "nvidia-auto-select".
(WW) Jul 05 21:49:22 NVIDIA(0): 
(II) Jul 05 21:49:22 NVIDIA(0): Validated modes:
(II) Jul 05 21:49:22 NVIDIA(0):     "nvidia-auto-select"
(**) Jul 05 21:49:22 NVIDIA(0): Virtual screen size configured to be 1680 x 1050
```

This situation is pathetic, as I am back to editing xorg.conf which in fact has no effect, only me wasting time. Whatever was in update has hosed resolution detection. EDID works fine as I can parse it with edid utility.

Now to use my computer I have to remove xorg.conf which puts it into vesa mode, where video playback is unbearable.

interesting that xrandr shows only up to 640x480 with all the other useless resolutions.

I am using nvidia_current driver from repository (jockey).

---

### Post by SergeiFranco on 2010-07-05
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9478859](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9478859)

> **Spr0k3t said:**
> After troubleshooting an issue with low resolution on the nvidia graphics with 3D hardware.  I've come across a temporary solution.

The problem: On boot, the error message "Could not apply the stored configuration for monitors X server does not support size requested" would show up and the resolution would be 640x480.

I found the problem is related to the nvidia-current 195.36.24-0ubuntu1~10.04 version.  So, I rolled back the version to 192.36.15-0ubuntu2 version and locked the version.  The same had to be done with nvidia-current-modaliases.

I'm checking to see if there's a bug posted regarding this.

---

### Post by tigerglebe on 2010-07-05
> **SergeiFranco said:**
> [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9478859](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9478859)

On mine I can't even go that high version wise.  Hardware is too old.  Version available is 96.

---

### Post by rollin on 2010-07-05
Hi OP! I think there is some debate whether the drivers from nvidia are the most up to date but they worked for me on some hardware I was struggling with recently.

Just go to [www.nvidia.com]("http://www.nvidia.com"). Download the driver to your home directory or whatever. Go to tty 1, and kill the x session, using the commands:
```

Ctrl+Alt+F1
sudo /etc/init.d/gdm stop
```Now cd to the directory where you downloaded the file and the command to install is:

```
sudo sh <name of NVIDIA driver>
```Personally I had some hash sum mishmatches at this stage due to the download in FF, so I ended up downloading it with wget and the installation went smoothly. I rebooted after this and removed the proprietory drivers and everything was good, proper resolution etc!

---

### Post by tigerglebe on 2010-07-05
> **rollin said:**
> Hi OP! I think there is some debate whether the drivers from nvidia are the most up to date but they worked for me on some hardware I was struggling with recently.

Just go to [www.nvidia.com]("http://www.nvidia.com"). Download the driver to your home directory or whatever. Go to tty 1, and kill the x session, using the commands:
```

Ctrl+Alt+F1
sudo /etc/init.d/gdm stop
```Now cd to the directory where you downloaded the file and the command to install is:

```
sudo sh <name of NVIDIA driver>
```Personally I had some hash sum mishmatches at this stage due to the download in FF, so I ended up downloading it with wget and the installation went smoothly. I rebooted after this and removed the proprietory drivers and everything was good, proper resolution etc!



Linux Display Driver - x86
 
 

Version:
	
96.43.16
Release Date:
	
2010.02.11
Operating System:
	
Linux
Language:
	
English (U.S.)
File Size:
	
14.5 MB 


Only option given.  Same driver as comes with Ubuntu.

---

### Post by rollin on 2010-07-05
> **tigerglebe said:**
> Only option given.  Same driver as comes with Ubuntu.

Oops, that sucks then! If you want an older version I managed to change the language to UK and found: [http://www.nvidia.co.uk/object/linux_display_ia32_100.14.11_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_100.14.11_uk.html)

In all honesty I've only begun learning about graphics cards and drivers so I don't know if a UK variant would be completely incompatible? 
I wish you luck with fixing the issue all the same! I know how irritating errors in screen res can be ](*,)

---

### Post by tigerglebe on 2010-07-05
> **rollin said:**
> Oops, that sucks then! If you want an older version I managed to change the language to UK and found: [http://www.nvidia.co.uk/object/linux_display_ia32_100.14.11_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_100.14.11_uk.html)

In all honesty I've only begun learning about graphics cards and drivers so I don't know if a UK variant would be completely incompatible? 
I wish you luck with fixing the issue all the same! I know how irritating errors in screen res can be ](*,)

I'll get on with it and see if it works in the morning.  Thank you.

---

### Post by rollin on 2010-07-06
> **tigerglebe said:**
> I'll get on with it and see if it works in the morning.  Thank you.

You're welcome, I just hope it doesn't spit out loads of errors #-o

---

### Post by tigerglebe on 2010-07-06
> **rollin said:**
> You're welcome, I just hope it doesn't spit out loads of errors #-o


Didn't work.  Let's just hope that Ubuntu can fix this nasty bug soon as I'd hate to have to move to another distribution (like Mandriva where it works fine).

---

### Post by jounihat on 2010-07-06
Hey, my laptop's X crashed yesterday and I had to reboot. After the reboot my Samsung Syncmaster P2770H couldn't be recognized anymore (or it was recognized as a lousy laptop screen). I have Intel's integrated graphics card (940 I guess). I was able to fix the problem with xrandr (code below), but I want to know is this a Ubuntu issue or a monitor issue? I'm putting my money on Ubuntu, because it occured right after the X crash.

Fix (on 27" full-hd display, alter to match your own display):
$ xrandr --newmode fullhd 148.50 1920 2008 2052 2200 1080 1084 1088 1125
$ xrandr --addmode VGA1 fullhd

---

### Post by rollin on 2010-07-06
> **tigerglebe said:**
> Didn't work.  Let's just hope that Ubuntu can  fix this nasty bug soon as I'd hate to have to move to another  distribution (like Mandriva where it works fine).

Sorry to hear that. I like Mandriva but agree being forced to switch OS due to major bugs sucks ... 
Last thoughts...  use "alien" to convert Mandriva rpm driver to deb or maybe try 9.10 which was the only option for me. Good luck all the same!

---

### Post by tigerglebe on 2010-07-06
> **jounihat said:**
> Hey, my laptop's X crashed yesterday and I had to reboot. After the reboot my Samsung Syncmaster P2770H couldn't be recognized anymore (or it was recognized as a lousy laptop screen). I have Intel's integrated graphics card (940 I guess). I was able to fix the problem with xrandr (code below), but I want to know is this a Ubuntu issue or a monitor issue? I'm putting my money on Ubuntu, because it occured right after the X crash.

Fix (on 27" full-hd display, alter to match your own display):
$ xrandr --newmode fullhd 148.50 1920 2008 2052 2200 1080 1084 1088 1125
$ xrandr --addmode VGA1 fullhd

I might try this but not sure what the 148.50 is.  I recognize the others as being the first part of the resolution supported.

---

### Post by tigerglebe on 2010-07-07
Found a fix!  Apparently if you go into Software Sources and go under the Updates tab there is an option for Pre-Released Updates.  Check mark that and click close.  It'll run an update to your sources.  Then go to Update Manager and check for updates.  Apply all updates and reboot.

Apparently it WAS an Ubuntu bug that is being fixed.  Back to glorious 1400x1050 for me!

---

### Post by richardpd on 2010-11-29
I have the same problem -Monitor Unknown
& am stuck with 800x600 resolution.

I tried updating (pre-released also) & apparently am up to date but still have unknown monitor! Help!

Anyone have any other ideas to get my monitor detected & increase screen resolution?
I am grateful for helpful replies, many thanks

-----------------------------------------------------
Ubuntu-Uwhatu

---

### Post by naught101 on 2011-01-26
Here's what I've got. Run ```
cvt -r 1680 1050
```
That will give you some output like:
```
# 1680x1050 59.88 Hz (CVT 1.76MA-R) hsync: 64.67 kHz; pclk: 119.00 MHz
Modeline "1680x1050R"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync
```
Take that last line, excluding the "Modeline" at the start, and create a new mode using xrandr (the "1680x1050N" in the example below is just a name).
Then add that mode to your monitor (VGA1 on my system, find out which it is on yours with "xrandr --list").
Then apply it:
```
xrandr --newmode "1680x1050N"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync
xrandr --addmode VGA1 "1680x1050N"
xrandr --output VGA1 --mode "1680x1050N"
```

---

