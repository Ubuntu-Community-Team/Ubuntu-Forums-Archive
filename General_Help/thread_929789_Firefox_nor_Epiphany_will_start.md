---
title: "Firefox nor Epiphany will start"
date: 2008-09-25
forum: General Help
---

### Post by toyota_f1 on 2008-09-25
Ubuntu 8.04 64bit

After most recent round of updates my firefox won't work. I tried to replace with Epiphany but neither will start.  Amazingly IE4Linux version of IE6 will not start either.  Not sure on the IE (only a web dev item for me, not a necessity) - but the Firefox and Epiphany both produce only the very basic

user@user-linux: -$ firefox
Segmentation fault

with no other info.  Rebooting does not help.  I deleted the .mozilla directory, removed and reinstalled the packages with Synaptic, also removed SCIM, libflashsupport, and flashplugin-nonfree per other posts with no improvement.

Any assistance would be quite valuable as this is my work machine and I can't afford to go through a reinstall to fix what is hopefully something simple (plus a reinstall is an ugly way to fix a problem that I haven't had to go through since switching to ubuntu at Dapper).

Thanks for any help or ideas!

---

### Post by LowSky on 2008-09-25
[http://ubuntuforums.org/showthread.php?t=23433](http://ubuntuforums.org/showthread.php?t=23433)

Mozplugger might be the issue

this might help too
[http://locoteam.ubuntuforums.org/showthread.php?t=556321](http://locoteam.ubuntuforums.org/showthread.php?t=556321)

---

### Post by toyota_f1 on 2008-09-25
None of this worked for me, I don't have SCIM installed and not using Mozplugger... is there any good way to debug and see what specifically is killing it?

If I click the icon just get the window at the bottom showing "Starting Firefox Web Browser" which disappears after a few seconds.

Could it be a bad stick of RAM?  I'm just remoting into the box now so I can't restart it and fire up memtest until tomorrow.

---

