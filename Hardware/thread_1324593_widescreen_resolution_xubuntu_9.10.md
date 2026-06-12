---
title: "widescreen resolution xubuntu 9.10"
date: 2009-11-12
forum: Hardware
---

### Post by Miscellaneous on 2009-11-12
Hi.


First of all, I know there are a lot of [resolved] threads related to that topic already. In my opinion: none of them work. I am going round in circles. Please help!

I am trying to plug my widescreen TV into my baby-dell (optiplex sx260). I can only display 4:3 ratios at the moment. The max refresh rate the TV supports seems to be 60Hz.

Obviously the GUI tool does not offer any widescreen 60Hz mode.


--------------------


Here is my **system**:
Linux hostname 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

I have installed the **Intel driver** I found on some thread in this forum:
$ dpkg -l xserver-xorg-video-intel
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name            Version         Description
+++-===============-===============-==============================================
ii  xserver-xorg-vi 2:2.9.0-1ubuntu X.Org X server -- Intel i8xx, i9xx display dri


-----------------------


I have tried setting the driver to "Intel" and setting the resolution in **xorg.conf**, it seems to be completely ignored:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth		1
		Modes		"1152x864"
	EndSubSection
EndSection


---------------------


I tried installing **915resolution** as specified on this forum as well: can't find the package.


----------------------


I also read this [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
I tried **xrandr**: it does nothing at all. For example if I type xrandr and pick one of the possible resolutions (even 4:3 ratio), and then type:
$(sudo) xrandr --output LVDS --mode 1152x864 --rate 60
nothing happens.
I added a modeline anyway for the heck of it:
$ cvt 1152 864
# 1152x864 59.96 Hz (CVT 1.00M3) hsync: 53.78 kHz; pclk: 81.75 MHz
Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
$ xrandr --newmode "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2048 x 2048
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
  1152x864_60.00 (0xf9)   81.8MHz
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.8KHz
        v: height  864 start  867 end  871 total  897           clock   60.0Hz
$ xrandr --output LVDS --mode 1152x864_60.00

Nothing happens. I guess it's normal since the X settings are just ignored. All I want to know is where the settings are... It's not using the xorg.conf file and there's no monitors.xml under .config either...

---

### Post by Bunnybugs on 2009-11-12
> **Miscellaneous said:**
> Hi.


First of all, I know there are a lot of [resolved] threads related to that topic already. In my opinion: none of them work. I am going round in circles. Please help!

I am trying to plug my widescreen TV into my baby-dell (optiplex sx260). I can only display 4:3 ratios at the moment. The max refresh rate the TV supports seems to be 60Hz.

Obviously the GUI tool does not offer any widescreen 60Hz mode.


--------------------


Here is my **system**:
Linux hostname 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

I have installed the **Intel driver** I found on some thread in this forum:
$ dpkg -l xserver-xorg-video-intel
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name            Version         Description
+++-===============-===============-==============================================
ii  xserver-xorg-vi 2:2.9.0-1ubuntu X.Org X server -- Intel i8xx, i9xx display dri


-----------------------


I have tried setting the driver to "Intel" and setting the resolution in **xorg.conf**, it seems to be completely ignored:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
    Driver        "intel"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Depth        1
        Modes        "1152x864"
    EndSubSection
EndSection


---------------------


I tried installing **915resolution** as specified on this forum as well: can't find the package.


----------------------


I also read this [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
I tried **xrandr**: it does nothing at all. For example if I type xrandr and pick one of the possible resolutions (even 4:3 ratio), and then type:
$(sudo) xrandr --output LVDS --mode 1152x864 --rate 60
nothing happens.
I added a modeline anyway for the heck of it:
$ cvt 1152 864
# 1152x864 59.96 Hz (CVT 1.00M3) hsync: 53.78 kHz; pclk: 81.75 MHz
Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
$ xrandr --newmode "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2048 x 2048
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
  1152x864_60.00 (0xf9)   81.8MHz
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.8KHz
        v: height  864 start  867 end  871 total  897           clock   60.0Hz
$ xrandr --output LVDS --mode 1152x864_60.00

Nothing happens. I guess it's normal since the X settings are just ignored. All I want to know is where the settings are... It's not using the xorg.conf file and there's no monitors.xml under .config either...

Well, at Ubuntu the settings come from the Videocard driver;)

Did you install that one?

---

### Post by Yellow Pasque on 2009-11-12
> $(sudo) xrandr --output LVDS --mode 1152x864 --rate 60
nothing happens.

The LVDS output is for your laptop panel. You probably want to use "VGA" to control an external screen. [http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950#External_display_with_XRandR](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950#External_display_with_XRandR)

---

### Post by Miscellaneous on 2009-11-12
Hi! Thanks for helping!



Bunnybugs:
I'm sorry but could you please talk to me like an idiot, because well, I am one. 
I thought that this Intel thing was already it... The xserver-xorg-video-intel package that I installed with apt-get. If I remember correctly I did that because Google told me those machines have an Intel video chipset or something along those lines.

So, what am I supposed to do to figure out what driver I need and how to install it? 



Temüjin:
Aaaaaah that's what it is? I was wondering what those letters meant!
If I try with VGA, nothing happens, if I try with VGA1, it says "cannot find mode 1152x864_60.00" (this line is still in the list when I type xrandr though).

---

### Post by Miscellaneous on 2009-11-15
Does anyone know how to set Xubuntu up for widescreen 60Hz when it's not in the GUI options?

---

