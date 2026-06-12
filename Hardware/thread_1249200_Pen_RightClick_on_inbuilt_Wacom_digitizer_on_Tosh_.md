---
title: "Pen RightClick on inbuilt Wacom digitizer on Tosh Satellite R10 (TabletPC) - Jaunty"
date: 2009-08-25
forum: Hardware
---

### Post by Roswellgrey on 2009-08-25
With Jaunty, most of the Wacom stuff works out of the box for me, but as with previous versions, the right click on the pen doesn't. 
With previous versions, an addition of 3 lines to xorg.conf is all that is required, but this has changed with Jaunty - xorg.conf is now *not* the place for Wacom tweaks

Now, there are some *very* long threads here discussing the Wacom on Jaunty, and I personally struggled to find how to *just* make the right click work. 

As such, thought it worth popping a solution to the problem here, in case anyone else struggles :)

1. make sure wacom-tools is installed via Synaptic
2. create a script file with the following commands:

#!/bin/bash
xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Button2 "button 3"
xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Button3 "button 3"
xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" Button1 "button 1"    

3. set the permissions of new script file to execute ( chmod +x <filename> )

4. add the above script to the session startup by adding to System->Preferences->Startup Applications

I know this is pretty obvious ( as its just using the old xorg tweaks in a new method ) :), but it took me a while to work it out ...

Hope it helps someone ...

---

### Post by Anstice on 2009-09-16
Thank you so much. This was really begining to become a pain. I switched to Openbox because there is not much screen real estate on my new Thinkpad X60. However, with the right-click function not working I had to use the Super + W combo to get the menu up.

---

