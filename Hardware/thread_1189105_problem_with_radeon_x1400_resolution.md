---
title: "problem with radeon x1400 resolution"
date: 2009-06-16
forum: Hardware
---

### Post by pagheca on 2009-06-16
Hi,

I have Jaunty installed on my Dell Inspiron 9400. Everything worked fine until I attached an external monitor. The system worked at 1900 x1200 automatically at installation time. Since I attached the external monitor, the display resolution is lower and I can't set anymore the original resolution as that resolution is no more available in the list.

Graphics Card: Ati Radeon x1400 256MB installed, WUXGA.
Monitor 17" Ultrasharp Wide Screen - max resolution; 1900 x 1200.
I run Ubuntu 9.04.

System->Preferences->Display gives the following setup:
Resolution: 1680 x 1050 (16:10) (this is the max res listed).

The problem persists when I detach the external monitor and reboot the computer.

Any idea? 

thanks, pagheca

---

### Post by pagheca on 2009-06-16
Actually (I'm not an expert on linux) I found the solution to recall the original display configuration

$ sudo dpkg-reconfigure -phigh xserver-xorg

... and reboot.

However, this doesn't resolve the problem. What actually happened? I would like to understand why as soon as I attach the external monitor (a Neovo F419 1280x1024) the driver seems to change and the LCD resolution is set to a lower value. 

thanks 
pagheca

---

### Post by pagheca on 2009-06-16
... and now, by looking around in the forum, I apparently sorted out also the problem with the resolution of the external monitor. Just in case someone need it (maybe trivial for anyone but not for me):

Suppose your monitor support 1280 1024 60 but this is not listed in your System->Preference->Display.
First:

[FONT=Courier New]$ gtf 1280x1024 at 60Hz
[/FONT]
gives the following output (depending on the parameter set in the previous command)

[FONT=Courier New]# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 KHz; pclkl 10.88 MHz
Modeline [COLOR=Red]"1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
[/COLOR][/FONT]
Now you have to read the name of the VGA port. You use the following command:
[FONT=Courier New]
$xrandr[/FONT]

that in my case gives the following output. Note the part in red:

[FONT=Courier New]Screen 0: minimum 320 x 200, current 3200 x 1200, maximum 3200 x 1200
[COLOR=Red]VGA-0[/COLOR] connected 1280x1024+1920+176 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   LVDS connected 1920x1200+0+0 (normal left inverted right x axis y axis) 367mm x 230mm
   1920x1200      60.0*+
   1920x1080      60.0  
   1600x1200      59.9  
   1680x1050      60.0  
   1400x1050      60.0  
   1440x900       59.9  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)
[/FONT]
Just copy the part after Modeline (that I set in [COLOR=Red]red[/COLOR]) in the following command:

[FONT=Courier New]$ xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync[/FONT]

At this point:[FONT=Courier New]

$xrandr --addmode VGA-0 1280x1024.
[/FONT]
Set the resolution by using System->Preferences->Display for the 2 monitors. You maybe required to logout and login. This last sequence was  required a couple of times in my case but at the end I got both the external and LCD monitor running at their highest resolutions.

Hope it doesn't contain errors and may help newbies like me.

pagheca

---

