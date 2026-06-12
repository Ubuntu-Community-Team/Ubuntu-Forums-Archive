---
title: "Mouse and Keyboard problems after Update"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by FBoeckle on 2009-05-05
Hi all,

I've updated my xUbuntu from 8.04 to 8.10 . (Not going to 9.04 yet, since there are driver incompatibility :()

The problem is the following : When I start up the computer, all seems to work well, but the mouse and keyboard don't work, so I can't login. I've searched through this forum, and found a solution that nearly solves the problem :

When starting computer, boot first in recovery mode and open a root terminal shell. Then I have to type following cmds : 
> 
update-rc.d -f dbus remove
update-rc.d -f hal remove
update-rc.d -f dbus defaults
update-rc.d -f hal defaults
reboot
After that, it all works properly... until next time I start the computer again.

It seems to me there's a problem in some bootscript (though I might be wrong), and I was thinking about adding a bootscript that should be executed at the end of the boot process and that would run those commands. Or even better, to repair the defectuos script.
I've looked around on Internet and ubuntu forum about how to make such a script, but I don't understand all of it, and I'm a bit scared that I could do more harm than good.

FBoeckle

---

