---
title: "Laptop + External Dock"
date: 2008-12-15
forum: Hardware
---

### Post by BrandonBan6 on 2008-12-15
Hello,

I'm currently using a Lenovo T61 with the latest Nvidia Drivers (ver. 177) and it is working sweet. 

In the office, I use a docking station with external monitor. I then use the Laptop Screen and External Monitor for "dual screens", i.e. twinview in Nvidia Settings. The painful part is when I un-dock, and boot the laptop, it boots in "twinview" still, and the Logon field is off the laptop screen. So, to fix it, I reload the xorg.conf file and the next day, I re-set up the Nvidia Settings for twinview. This is quite painful. 

Can I set a profile for Nvidia settings that will load the appropiate display profile depending on how the laptop boots? 

Or can I set Nvidia to auto-detect and enable any external monitor? 

or any other solutions that have expanded beyond my newb scope? 

I searched around the forums and google, but hadn't found a real answer, but if I missed a post on this already, I apologize. 

thanks!

---

### Post by BrandonBan6 on 2008-12-16
Or perhaps I can write two scripts, one for my "default" display and one for my "dual monitor" display? Any thoughts?

---

### Post by InlawBiker on 2008-12-18
I also have a T61 with Nvidia NVS-140m with the advanced dock, same driver as you.  I use an external monitor when attached to the dock.  

I've come to the conclusion that it just doesn't work well with Linux.  You'll notice that in Vista or XP that Lenovo has written lots of drivers and tools to make sure your display works no matter what you do.  Even then it's flakey - it forgets if the external monitor is left or right, or which is the primary.  But mostly it works.

So this is how I mostly use it in Linux.

80% - use only the external display, disable laptop display.  I set this using the nvidia control panel.  The Nvidia control panel will remember that you only want to use the external display and boot that way if you're docked.  Undocking doesn't work - I power it down, remove it from the dock and reboot.  The laptop screen always shows up for me when I boot undocked.

10% - use twin-view with the laptop's LCD plus the external LCD.  I only do this if I'm going to work without undocking for a while.  Once it's running it works fine.  To undock I power down, remove from dock, then boot free of the dock.

10% Vista when necessary.  Dual-display always works.

If you're undocking or re-docking it has always required a reboot for me to work right.  It's never just "worked."  Restarting gdm doesn't help, it needs to reboot.

Again I blame this on nvidia putting 99% of their effort into Windows drivers & software and precious little on Linux.  I don't experience your problem, where the computer thinks the external display is attached even when it's not.  But that's probably because I almost always just use the external display.  Twin-view has been too big of a pain to mess with it.

---

### Post by BrandonBan6 on 2008-12-19
Thanks InlawBiker, I suppose your analysis of the Nvidia and Windows is correct...I was just hoping for better out of linux. You bring up some good and interesting points there with Nvidia...Maybe someday, we'll have drivers that just work!

I found that if I don't mod the xorg.conf file with the Nvidia-Settings GUI, that is, I just enable the external monitor to twin view and do not overwrite the xorg file nor restart the X session, then I can utilize the dual monitors function just fine. I just have to do that every morning, That isn't too bad of a problem I suppose, like you said, I would end up redoing it in windows!! Now if I could only get a decent MMC console going in Linux, and I'd be set!!! :D 

Thanks for the reply.

---

