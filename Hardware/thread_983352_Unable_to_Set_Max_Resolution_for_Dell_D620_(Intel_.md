---
title: "Unable to Set Max Resolution for Dell D620 (Intel 945GM)"
date: 2008-11-15
forum: Hardware
---

### Post by Jaybop on 2008-11-15
Hi all,

I like so many others am having difficulties changing to my maximum support resolution in Ubuntu 8.10 and so far, haven't had much luck with scraping threads for resolutions.  Some have given up or found funky drivers for their cards, but I'm hoping someone can provide a suggestion for my specific scenario.

As I said, I'm running Intrepid on a Dell D620 laptop with Intel 945GM:

**$ lshw -c display**
```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```


I believe I have the appropriate driver installed and in use:

**$ dpkg --list | grep -i intel**
```
ii  xserver-xorg-video-intel
2:2.4.1-1ubuntu10
X.Org X server -- Intel i8xx, i9xx display d
```

**$ glxinfo | grep -i renderer**
```
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061102 x86/MMX/SSE2
```


However, the **Screen Resolution** tool only displays: 640x480, 800x600, 1024x768, and 1280x800 (WXGA).  I am trying to set a resolution of 1440x900 (WXGA+).  Since my preferred resolution isn't a choice, I attempted to add it manually using xrandr:

**$ cvt -v 1440 900 60.0Hz**
```
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

**$ xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync**

.. and to verify..

**$ xrandr**
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 300mm x 190mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
  1440x900_60.00 (0xa8)  106.5MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
```

**$ xrandr --addmode LVDS "1440x900_60.00"**
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  17
  Current serial number in output stream:  18
```


This is where I am stuck.. I'm not sure if I need to optimize my manually entered resolution or go down a different road.  Any help would be appreciated!

---

### Post by Jaybop on 2008-11-15
.. or maybe I'm going down the wrong path.  Whatever the case, I'm new at Ubuntu (and Linux in general), so I've hit a dead end, heheh.

---

### Post by Yezinki on 2008-11-15
PM contact linux23dragon.....hes the man to fix your issue.

---

### Post by Jaybop on 2008-11-16
K, I PMed him and asked him to check out this thread.  Hopefully he can help me and others out.

---

### Post by thorsten79 on 2008-11-16
Hi there,

I have I would say, exactly the same problem.
I tried with two different Laptops (first Thinkpad t40 with a Radeon 7500, second Macbook with Intel x3100). I was not able to get my external flatscreen (Benq FP767) to run with its maximum resolution (1280x1024), the max I could use was 1024x768. Xrandr dit simply not show the 1280x768. Is there another way to tell the system which max-resolution the TFT can handle? Interestingly the screen works perfectly under Ubuntu when it is directly connected to a desktop computer ...

Anz Ideas?

---

### Post by linux23dragon on 2008-11-17
Its been a while since I have serviced this issue.

This should allow you to pick both the driver (intel) and the resolutions you want.


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

More information about wide screen resolutions:- 

***_[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+widescreen+laptop[/COLOR]_***

Hope that helps.

---

### Post by icanfly0307 on 2008-11-17
In a terminal, type in displayconfig-gtk. This should bring up a dialog box allowing you to choose your laptop monitor. Select the one which has your resolution, something like, Generic Laptop Screen (Screen Resolution). Hope this helps!

---

### Post by Jaybop on 2008-11-18
Hmmm.. I'm slighty confused.. as I understand it, the [FONT="Courier New"]sudo dpkg-reconfigure -phigh xserver-xorg[/FONT] command just regenerates the xorg.conf back to its default values.  My xorg.conf hasn't changed at all and there was no program that allowed me to choose the driver or set my desired resolution.

My Xorg.conf is just..
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

I've read in other threads/boards that the command used to bring up a selection of menus, but nothing happens in 8.10 when I run it.  That goes for 915resolution as well.. it's not in 8.10. :(


@icanfly0307:
I believe this command has been removed from intrepid.

---

### Post by Jaybop on 2009-04-29
Argh.. still not working, even in Jaunty. :(

---

### Post by RgnKjnVA on 2009-05-08
If you haven't already, check out this bug report in Launchpad. Please consider adding your info as they've toyed with closing the issue due to lack of info.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/189694](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/189694)

---

### Post by simormate on 2009-05-08
This solution worked great for me. I managed to restore original resolution after messing everything up while trying to get the right resolution for s-video output.

laptop: fujitsu-siemens esprimo mobile m9400
video-card: intel x3100, gm965 chipset

> **linux23dragon said:**
> Its been a while since I have serviced this issue.

This should allow you to pick both the driver (intel) and the resolutions you want.


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

More information about wide screen resolutions:- 

***_[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+widescreen+laptop[/COLOR]_***

Hope that helps.

---

### Post by riceandlentils on 2009-08-19
I have a dell d620 with he same chipset and also can't get the resolution right. Xorg says I have a generic monitor.
:confused:

---

