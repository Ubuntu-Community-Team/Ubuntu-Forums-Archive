---
title: "Installation on old Sony Vaio AIO unable to use full display"
date: 2019-10-27
forum: Hardware
---

### Post by stuffofinterest on 2019-10-27
I have a very, very (I think about 12 years) old Sony Vaio AIO (model VGC-JS160J, part # PCG-2F2L) that was recently retired from its primary role.  Under Windows Vista it was running so slow as to be almost unusable.  Rather than shipping the computer off to recycling, I thought I take a stab at loading up Ubuntu to see if it could give some new life to an old computer.

Everything seemed to go OK until I went to configure the display setup.  The screen is a 20" 1680x1050 resolution, but the OS detects the screen as 1600x1200.  This leaves a black bar on the side and the bottom of the display areas (including the "start" button) hidden.  The problem was present with both Ubuntu 18.04.03 and 19.10.  After rebuilding the OS twice on the machine I'm sitting on 19.10 now.

After some research I tried using these commands to add the correct display mode:

```

sudo cvt 1680 1050 60
xrandr --newmode "1680x1050_60.00" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode LVDS-1 1680x1050_60.00

```

This fixed the bottom of the display, but the right side disapeared under a dead section of the display.  The dead section is usually black but one time when I was using xrandr commands to switch modes it switched to magenta.  The virtual space is there as the menu options normally in the top-right corner were hidden, but nothing displays on that side.  I next added in another mode for 1600x1050 with this:

```

sudo cvt 1600 1050 60
xrandr --newmode "1600x1050_60.00" 140.00  1600 1704 1872 2144  1050 1053 1063 1089 -hsync +vsync
xrandr --addmode LVDS-1 1600x1050_60.00
xrandr --output LVDS-1 --mode 1600x1050_60.00

```

Now the right edge of the virtual display is against the black bar with no content hidden.  From that, it looks like something in the driver won't take the display beyond 1600 pixels wide.

After reading through far too many forum posts, I can see some common information asked for in these situations.  First, here is the output from "lspci -nnk | grep -iA2 vga"

```

00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03)
    Subsystem: Sony Corporation 4 Series Chipset Integrated Graphics Controller [104d:9044]
    Kernel driver in use: i915

```

Next, here is the output from "xrandr -q" after adding the modes above:

```

Screen 0: minimum 320 x 200, current 1600 x 1050, maximum 8192 x 8192
LVDS-1 connected primary 1600x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200     60.00 +
   1600x1050_60.00  59.96* 
   1680x1050_60.00  59.95  
VGA-1 connected (normal left inverted right x axis y axis)
   1024x768      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  

```

Hopefully, someone will have an easy fix.  On the good side, the PC has a great new spring in its step with Ubuntu.  Responsiveness is great and for basic functions like web browsing, video playing, and document editing it should be good for years more.  Just need to solve this display issue.  Speaking of which, I'll need to come up with a way to make the setting persistent.  I know I can put the commands in the ".profile" file, but it would be nice to have something that applies to all accounts instead of having to do the settings for every user.  I've worked with Linux for over 20 years, dating back to the pre 1.0 days on floppy disks, but my *nix skills have grown far too rusty.

Thanks for any help.

---

### Post by mörgæs on 2019-10-27
Hi, welcome to the fora.

Though it does probably not solve the resolution problem I still think you will be better off using a lighter Buntu like Mate/Lubuntu/Xubuntu. The Sony has an Eaglelake graphics processor which might be a little to the weak side when running Ubuntu.

---

