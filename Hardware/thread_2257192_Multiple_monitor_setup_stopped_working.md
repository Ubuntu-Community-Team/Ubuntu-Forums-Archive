---
title: "Multiple monitor setup stopped working"
date: 2014-12-17
forum: Hardware
---

### Post by James_Creasy on 2014-12-17
I had set up my Ubuntu 14.04/Unity on a Dell M4800 with two external monitors,one connected on HDMI and one on VGA. I had some initial problems with refresh on the HDMI monitor, mouse leaving tracks and slow response, which was fixed by installing nVidia proprietary drivers through the Software & Updates UI. I might have also run some terminal commands, hard to remember since it's a process of experimentation getting stuff to work usually.

A few days ago the HDMI monitor would not show an image. I tried about 10 different configurations, starting with remove --purge nvidia-* to get back to the default driver. This resulted back to the slow/bad refresh on the HDMI-connected monitor, installing the 331.113 driver (proprietary, tested) resulted in refusal to boot a UI, terminal only. The other driver 331.113 (proprietary) boots in mirror displays mode, changing to multiple monitors causes the desktop surface to be stretched and the mouse not usable, although the side and top bars looked and acted normally. 

I tried many other configurations, bumblebee, etc. with no good result.

Right now I'm booted with the 331.113 (proprietary) driver and one external monitor (VGA), the HDMI monitor is black.  

I'd like to get back use of both external monitors, anything else to try?

More info:

[SIZE=2][FONT=courier new]$ lspci | grep VGA[/FONT][/SIZE]
[SIZE=2][FONT=courier new]00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)[/FONT][/SIZE]
[SIZE=2][FONT=courier new]01:00.0 VGA compatible controller: NVIDIA Corporation GK107GLM [Quadro K1100M] (rev ff)[/FONT][/SIZE]

and

[FONT=courier new]$ xrandr[/FONT]
[FONT=courier new]Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 32767 x 32767[/FONT]
[FONT=courier new]eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm[/FONT]
[FONT=courier new]   1920x1080      60.0*+   59.9     40.0  [/FONT]
[FONT=courier new]   1680x1050      60.0     59.9  [/FONT]
[FONT=courier new]   1600x1024      60.2  [/FONT]
[FONT=courier new]   1400x1050      60.0  [/FONT]
[FONT=courier new]   1280x1024      60.0  [/FONT]
[FONT=courier new]   1440x900       59.9  [/FONT]
[FONT=courier new]   1280x960       60.0  [/FONT]
[FONT=courier new]   1360x768       59.8     60.0  [/FONT]
[FONT=courier new]   1152x864       60.0  [/FONT]
[FONT=courier new]   1024x768       60.0  [/FONT]
[FONT=courier new]   800x600        60.3     56.2  [/FONT]
[FONT=courier new]   640x480        59.9  [/FONT]
[FONT=courier new]VGA1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 531mm x 299mm[/FONT]
[FONT=courier new]   1920x1080      60.0*+[/FONT]
[FONT=courier new]   1600x1200      60.0  [/FONT]
[FONT=courier new]   1680x1050      60.0  [/FONT]
[FONT=courier new]   1280x1024      75.0     60.0  [/FONT]
[FONT=courier new]   1440x900       59.9  [/FONT]
[FONT=courier new]   1280x960       60.0  [/FONT]
[FONT=courier new]   1152x864       75.0  [/FONT]
[FONT=courier new]   1024x768       75.1     70.1     60.0  [/FONT]
[FONT=courier new]   832x624        74.6  [/FONT]
[FONT=courier new]   800x600        72.2     75.0     60.3     56.2  [/FONT]
[FONT=courier new]   640x480        75.0     72.8     66.7     60.0  [/FONT]
[FONT=courier new]   720x400        70.1  [/FONT]
[FONT=courier new]DP1 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=courier new]HDMI1 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=courier new]VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/FONT]


Doing: 

[FONT=Ubuntu Mono]xrandr --output HDMI1 --mode 1024x768 --left-of eDP1


results in 

[/FONT][FONT=courier new]xrandr: Configure crtc 2 failed[/FONT]

---

### Post by James_Creasy on 2014-12-23
Update: installed the newest nvidia drivers (340) from the nvidia site but that caused the desktop to freeze after login. Also tried 310, no luck. Tried several others, ended up with weird stretched screen, not usable. Back to 331 but only my VGA external monitor works. 

I'm fairly sure an Ubuntu update broke this, so I might try blowing away the entire install and starting over. 

Both external monitors work fine in Windows 7 on the same machine (dual boot)

---

### Post by jeffjohn2 on 2015-01-11
I had succesfully mirrored HP v7 Notebook to TV using Ubuntu 12.04 but after updating to 14  I could only use screen-extend.  Eventually I had to revert to Ubuntu 12. Now working perfectly.

---

### Post by James_Creasy on 2015-12-21
It has been a year since my original post and have not yet had success with getting both monitors working correctly. Limping along with the Intel card also in the computer.

Installing the newest nvidia drivers caused Ubuntu desktop to hang on bootup, complete unresponsive. Unable to get a terminal window. Had to blow away my entire image and start with a new install of 14.04. Catastrophic.  

I've read many posts on this topic but not a fix yet. Any chance someone has found a fix by now? Thanks,

BTW- the Nvidia card is Quadro K1100M.

---

### Post by p.callan on 2016-01-01
Here is what I did:

[COLOR=#000000]I solved my own problem after some angst:[/COLOR]
[COLOR=#000000]In terminal:[/COLOR]

[B]xrandr --auto

[/B][B]This enabled the external monitor but the screens were mirrored. Went into system settings and there was only one monitor shown. After a second or two both screens appeared.
Turned off "mirror display".
Placed the screens as I wanted them.
Apply.[/B]

---

### Post by James_Creasy on 2016-01-05
Unfortunately, that had no effect for me. There are several problems:

1. Not able to reorder the monitors with System Settings- I can move the monitor up and down, but I can't drag it side to side. It always snaps back to the original location.
2. The mouse cursor is often invisible on my better working monitor (the VGA connected monitor)
3. The window close and other buttons are invisible/ missing. They still work- just not visible.
4. The display on the better monitor (VGA connected) is rasterized in some parts, particularly window outlines and tabs.
5. The HDMI connected monitor is barely usable- there is about a 2 second refresh delay, which makes typing difficult. Mouse movement leaves mouse cursor tracks over the screen.
6. I am not able to change the driver to an nVidia driver. It can select it, and the dialog looks right, but when I open it again, it's back to the Nouveau driver. Previously I tried over 10 different releases of the driver trying to find one that worked better. 

I've spent maybe 20 hours trying different combinations and suggestions. I think I have tried everything findable with a Google search.

The monitors work perfectly when booted into Windows 7.

---

