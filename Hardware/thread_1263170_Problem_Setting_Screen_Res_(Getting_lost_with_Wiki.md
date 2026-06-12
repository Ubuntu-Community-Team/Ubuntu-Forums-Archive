---
title: "Problem Setting Screen Res (Getting lost with Wiki Guide)"
date: 2009-09-10
forum: Hardware
---

### Post by ytene on 2009-09-10
Hi All,

I've been running Jaunty perfectly on an Acer Revo R3600, driving a Samsung 214T 21.4" (1600x1200) LCD Panel. Today I upgraded to a Dell 2408WFP (1920x1200) LCD Panel. For reasons I don't understand I've been unable to get my machine to work at the 1920x1200 resolution.

I am using VGA Connectivity through an Edimax KVM switch [but have tried it direct with no difference observed].

Running up in GNOME [ I typically use KDE ] I have tried to use the Preferences -> Display function to change screen resolution, but this only gives me an option up to 1600x1200 and does not auto-detect this monitor. Same results from System->System Settings with KDE. 

I have tried running up using the LiveCD and this also only goes to 1600x1200.

I have tried following the useful how-to in the wiki, here:-

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

and although the commands do seem to work, I am not able to achieve any changes to my display resolution. I'm pretty sure I'm missing something obvious and suspect I'm quite close, but can't quite see my way out of this. This is what I've done so far:-

# **cvt 1920 1200**
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync


# **xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync**


# **xrandr**
Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200       0.0* 
   1280x1024       0.0  
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
  1920x1200_60.00 (0x1c1)  193.2MHz
        h: width  1920 start 2056 end 2256 total 2592 skew    0 clock   74.6KHz
        v: height 1200 start 1203 end 1209 total 1245           clock   59.9Hz



# **xrandr --output 1920x1200**


Clearly the "cvt" and "xrandr --newmode" statements seem to be doing something, as I can see a reasonable-looking new display option appear in the xrandr summary listing. The step I'm missing is to understand what I need to do to access this new mode, and how I can make that a permanent option for all users booting this machine on this hardware.

Can anyone help to point me in the right direction please?

Thanks in Advance!

---

### Post by ytene on 2009-09-11
After a good night to sleep on the problem, I have managed to get just a little bit further:


1. Use the "cvt" command to poll the system for settings of the required resolution: 

# **cvt 1920 1200**
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00" 193.25 1920 2056 2256 2592 1200 1203 1209 1245 -hsync +vsync

2. Create a new Mode, utilising the settings returned from the "cvt" command:

# **xrandr --newmode "1920x1200_60.00" 193.25 1920 2056 2256 2592 1200 1203 1209 1245 -hsync +vsync**

3. Add the newly created mode to the "supported modes" list:

# **xrandr --addmode default 1920x1080_60.00**

4. [Try] to tell the display to utilise the new mode:

# **xrandr --output default --mode 1920x1080_60.00**

**[COLOR="Red"]xrandr: Configure crtc 0 failed[/COLOR]**

Right up until this point, everything seemed to be going really, really well. Then I get that final error message, shown in red, above. So before going further I verified my environment by using a Dell laptop to drive a 1920x1200 signal to the screen, which works fine.

I hope that the additional information will enable someone to help me cross the final hurdle.

Thanks in advance...

---

