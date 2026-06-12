---
title: "Multiple Displays in Ubuntu 8.10"
date: 2008-11-18
forum: General Help
---

### Post by cptsteiny on 2008-11-18
I just recently upgraded from 8.04 to 8.10.  When I was in 8.04, both of my displays were working properly.

I have two displays, an Insignia 19" which I had displayed at 1600x1200 (this was set as the Secondary display) and a Scepter 20" that I had displayed at 1680x1050 (this was set as the Primary display) using the NVidia drivers for a NVidia card that I can't quit remember exactly what type it is.  I had them both set to operate under the XOrg file as two seperate X servers.

When I first started operating Ubuntu 8.10, the resolutions of each screen were done properly and both screens looked normal. However, I was unable to launch any program in the Insignia 19" screen.  An error window would pop open which did not display any text, just "error" in the title bar of the window, and the system would freeze, sort of.  If I happened to have any programs open in the Scepter 20" display, I could still operate them, but I could no longer operate the two Gnome bars at the top and bottom, I also could not press the on/off button on the upper Gnome bar.  Ctrl-alt-delete and logging out seemed to correct everything back to the way it was.

My first step was to run the "NVIDIA X Server Settings" utility under "System" and "Administration".  However, initially I was unable to save any of the changes to the Xorg.conf file.  So I saved them to the desktop and then in a terminal moved them over to where they were supposed to be.  I then restarted the X Server, however, nothing changed.  I then went back to the "NVIDIA..." program and found that none of my changes from last time were there.  I should also point out that the NVIDIA utility had the arrangement of my monitors backwards from what my mouse was doing.  This all makes me think that Ubuntu is ignorning the Xorg.conf file completely.

After briefly searching the forums, I found out that Ubuntu is now trying to do away with the Xorg.conf file and should, under normal circumstances, be able to recognize and configure multiple displays automatically.  So, I went to the "System"->"Administration"->"Hardware Drivers" utility and disabled my NVIDIA driver.  After restarting the X Server, the Insignia display now no longer displays anything and the Sceptre display is at a lower resolution.  I then went to "System"->"Preferences"->"Screen Resolution".  However, the schematic says the display is "Unknown" (and only registers one display).  Clicking on the "Detect Displays" button does nothing.  Also, I cannot set the resolution any higher than 1280x960.

I've pretty much run out of things to try, does anyone have any suggestions?

Thanks!

---

