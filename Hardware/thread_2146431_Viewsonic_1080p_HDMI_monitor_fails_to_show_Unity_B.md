---
title: "Viewsonic 1080p HDMI monitor fails to show Unity Bar / Intel i3 NUC"
date: 2013-05-18
forum: Hardware
---

### Post by markMDW on 2013-05-18
[LIST]
[*]Intel QS77 Express Chipset 
[*]Intel Core i3-3217U Processor 
[*]Viewsonic VX2433wm monitor / 1080p [16:9 ratio] 
[*]Ubuntu 12.04 
[/LIST]

I'm using Ubuntu 12.04 with a Viewsonic VX2433wm monitor, its a 1080p [16:9 ratio] monitor that's connected with HDMI cable.  I installed the OS on a brandnew Intel Next Unit of Computing, model DC3217IYE, with integrated graphics. It appears that everything was detected and installed without a problem, except the zoom ratio of the display image to send to the monitor.  The monitor just barely shows the edge of the Unity sidebar. It appears that the view is zoomed in, cutting the sides, the top and the bottom away.  I can move my mouse pointer outside beyond the monitor display region.  The monitor does NOT allow me to fine tune the image position or size though it's settings, at least when connected with HDMI.  It has to be done within the OS.  

BTW, this monitor worked perfectly with another computer and Ubuntu 10.04 and its VGA/DVI cable.

I discoverd the Ubuntu 12.04 settings that allowed me to change the resolution from the default of 1920 x 1080 [16:9 ratio] to other resolutions.  I experimented and found that selecting 1680 X 1050 [16:10 ratio] works fine.  When I leave it at this, however, the monitor repeatedly pops up it's on dialog letting me know that the resolution isn't set correctly, that the monitor is designed to be using 1920 X 1080, which is the original resolution Ubuntu sets up for it--but like I had said, that [16:9] resolution doesn't show the Unity sidebar or edges, except for a tiny edge of the bar.

What's going on with my monitor and resolution, and how do I set it up properly?  Thanks for everyone's advice.  In the mean time I will just ignore the monitors repeated warnings that my resolution isn't set porperly.

--UPDATE--
SOLVED:  I just installed Ubuntu 13.04 (erasing Ubuntu 12.04) and the monitor problem has disappeared altogether.  I had thought I installed 13.04, but it turns out that it was Ubuntu 12.04.  The glitch is in Ubuntu 12.04, but NOT in Ubuntu 13.04.

---

### Post by markMDW on 2013-05-19
It turns out that the problem is with the Viewsonic monitor.  There are four unlabeled control buttons on the side that serve for changing its settings.  If the user inadvertently presses the fourth button down, it changes the monitor's mode from HDMI-PC mode to HDMI-AV mode, and in the later mode the display problem occurs--the display is too small to see the edges.   If the user presses that button again, it still won't revert back to the needed HDMI-PC mode.  It's just one-way toggel TO the HDMI-AV mode that fails. 

 It would be nice if the monitor had a one button press option to revert back to the proper mode, but it doesn't.  Instead, the user has to drill down through the monitors menus, select the Input Mode category, then select the HDMI-PC mode, then presto, it's fixed.   I had no idea that HMDI had more than one mode on this monitor, but now I do :-)     I don't know what the other mode is good for.

Side note --  I've got Ubuntu 13.04 installed right now, but I'm going back to Ubuntu 12.04.02 LTS because the sound doesn't work. I've researched it and there is a bug in the Ubuntu Kernel affecting HDMI sound.  Apparently I could install an alternative Kernel, but instead I'm opting for the LTS version.  (I'd be worried new problems would sprout up with another Kernel)

---

