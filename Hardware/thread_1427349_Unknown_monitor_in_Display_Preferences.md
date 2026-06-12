---
title: "Unknown monitor in Display Preferences"
date: 2010-03-11
forum: Hardware
---

### Post by danno3 on 2010-03-11
I have a Gateway GT5224 that uses onboard video Intel 950 GMA. When I go to Display Preferences, Monitor is Unknown and only 800x600 or 640x480 appears under Resolution and Refresh rate only shows 60hz (I'm using an old 17" CRT monitor - hey, don't laugh:wink:).

It appears that only a generic VGA video driver is being used an I'm unable to install the Intel GMA 950 driver - in fact, I can't even find the option to install it. I tried following the Ubuntu Pocket Guide, but when I went into Hardware Drivers, it shows "No proprietary drivers are in use..." and nothing shows. I tried searching online for Intel 950 video drivers for Linux, and didn't find anything.

---

### Post by danno3 on 2010-03-13
> **danno3 said:**
> I have a Gateway GT5224 that uses onboard video Intel 950 GMA. When I go to Display Preferences, Monitor is Unknown and only 800x600 or 640x480 appears under Resolution and Refresh rate only shows 60hz (I'm using an old 17" CRT monitor - hey, don't laugh:wink:).

It appears that only a generic VGA video driver is being used an I'm unable to install the Intel GMA 950 driver - in fact, I can't even find the option to install it. I tried following the Ubuntu Pocket Guide, but when I went into Hardware Drivers, it shows "No proprietary drivers are in use..." and nothing shows. I tried searching online for Intel 950 video drivers for Linux, and didn't find anything.
BTW, I have tried to edit /etc/X11/xorg.conf, but it doesn't exist.  I also ran lscpi | grep VGA and Ubuntu detects the video as Intel 82945G/GZ IGC (rev 02).  I know that when I checked online, the specs show that the video is onboard Intel 950 GMA.  Not sure what else to try.

---

### Post by danno3 on 2010-03-13
> **danno3 said:**
> BTW, I have tried to edit /etc/X11/xorg.conf, but it doesn't exist.  I also ran lscpi | grep VGA and Ubuntu detects the video as Intel 82945G/GZ IGC (rev 02).  I know that when I checked online, the specs show that the video is onboard Intel 950 GMA.  Not sure what else to try.
I also checked with Software Sources, and under the Ubuntu tab, all were checked (except for Source code), including Proprietary drivers for devices.  I even checked the Ubuntu cd-rom.  In the other Software, I checked the non-source options (I believe they were previously enabled).

I also checked Synaptic Package Manager and all the xserver-xorg-video drivers are installed, including the '-intel' (Intel i8xx, i9xx display driver).

---

### Post by efflandt on 2010-03-13
VGA is still not as plug and play as DVI or HDMI, so you may need to add a mode you want.

See what X finds for it in /var/log/Xorg.0.log and see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

That helped me set up similar Intel mobile resolution when I connect my laptop to an external HDTV (which defaults to 1024x768 that can display on both displays).  However, I use xrandr commands for that in a script run when needed, and am not sure how to make that permanent in Ubuntu 9.10 (which by default has no xorg.conf).  For a 1080p display, I actually had to get a modeline from Xorg.0.log of a DVI to HDMI desktop, because the modeline returned by cvt was horizontally scrunched.

I imagine your device for xrandr commands is VGA1, but see what just plain **xrandr** shows for it.

---

### Post by danno3 on 2010-03-14
Thanks for the info.  Xorg.0.log contained endless lines for each resolution and refresh rate combination, all of them showing "intel(0): Not using default mode "<hor>x<vert>" hsync out of range and "...vrefresh out of range".  The only modelines recognized were the 800x600_60 and 640x480_60.

I tried using cvt 1024 768 75 and copied/pasted the results as described in your wiki link, but attempts to use "xrandr --newmode..." always failed with something like "output mode not found", so I gave up on that and edited /etc/X11/xorg.conf and added modelines there.  Now I was able to select 1024x768 and 75 for Refresh Rate under Display Preferences.

It appears that cvt is not calculating horizontal and/or vertical scan frequencies correctly, because when I now choose that mode, the screen display is badly malformed.  I know 1024x768 at both 75 and 85 refresh rates work and display properly (in Win XP) and have been already been properly sized vertically and horizontally via the hardware settings on the monitor and I believe those are saved in the monitor hardware (or firmware).

Any solution for getting the correct modelines into xorg.conf so 1024x768_75 or _85 will render properly?

---

