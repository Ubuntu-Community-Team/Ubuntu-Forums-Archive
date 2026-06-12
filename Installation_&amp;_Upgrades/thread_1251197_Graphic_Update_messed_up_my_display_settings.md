---
title: "Graphic Update messed up my display settings"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by seb.el on 2009-08-27
Yesterday I had an automated updated request. (I always install them.)

I cannot tell what it was called, but it was something about graphics. Now my two displays can not be displayed anymore, get only one working. Any idea - same issue¿?

---

### Post by seb.el on 2009-08-27
CompuMax with Intel Core2Duo 2.8Mhz
4GB RAM
MSI Graphics Card NX8400GS 512MB DDR2 nVidia GeForce
2x Samsung Displays SyncMaster 2243 LNX
Ubuntu 9.04

---

### Post by NoaHall on 2009-08-27
You need to run "gksudo nvidia-settings" and change the settings and then save to x

---

### Post by seb.el on 2009-08-27
Thanks for your quick response.

I found those settings and when I want to "apply" the second display as the first one with "TwinView" or "Seperate X screen" I receive this error message:

[I]"The current settings cannot be completely applied due to one or more of the following reasons:

- The location of an X screen has changed.
- The location type of an X screen has changed.
- The colour depth of an X screen has changed
- An X screen has been added or removed.
- Xinerama is being enabled/disable.

For all the requested settings to take effect you must save the configuration to the X config file and restart the X server."[/I]

That might be right, but I don't understand. Could somebody redefine this advice?
What should I do in detail?

It would be great to get it back running again!
Sebas.

---

### Post by NoaHall on 2009-08-27
You did run it as gksudo right?
Try "sudo nvidia-settings" and do the same.

---

### Post by seb.el on 2009-08-27
Yes, it seems to me there are different ways to actually access the same setting mask. 

I tried it via Applications->Accessories->Terminal typing those sudo commands mentioned above. But it's the same mask and the same error message as from the "configure display settings" System->Preferences->Display. 

Well, using the one mentioned second I first get this error message: 
[I]
"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?"[/I]

If I click "yes" I get the same as the one mentioned above.
If I click "no" I get the Ubuntu standard display preferences, which I used to use for configuring the displays in the first place... But this one does not see my second display any longer at all :(

---

