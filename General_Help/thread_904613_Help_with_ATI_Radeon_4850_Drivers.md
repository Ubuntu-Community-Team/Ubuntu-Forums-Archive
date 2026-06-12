---
title: "Help with ATI Radeon 4850 Drivers"
date: 2008-08-29
forum: General Help
---

### Post by Tixer on 2008-08-29
So I installed the ATI binary drivers for my card, first through envy-ng and then manually. When I did it the first time with envy, rebooting gave me a black screen with a locked X session. I then attempted to remove that and install it manually, which took forever (but I did succeed). Unfortunately, that also gave me a locked X session on boot.

I found a post on the Arch Linux forums that suggested that 4 gigs of RAM or more was causing the problem, so I removed one of my 2 gig sticks and managed to boot to my desktop.

Catalyst says the driver is in use, but for some reason I can't use compiz, because I get a white screen and a cursor whenever I enable it.

Any suggestions for solving either problem?

---

### Post by onfyreforjesus on 2008-09-02
look here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

uninstall any drivers installed by envy before going to this guide. After a successful installation, try putting back the 2 GB stick. compiz, video playback and 3d games should work!

Be careful to follow all instructions faithfully. If catalyst 8.8 doesnt work for you try 8.7 and 8.6.


Also head over to the phoronix.com forums and the catalyst 8.8 drivers discussion. There is something about a nopat option these guys were talking about. Wine games should play well too.

[http://www.phoronix.com/forums/forumdisplay.php?f=19](http://www.phoronix.com/forums/forumdisplay.php?f=19)




All the best! :)
hopefully after following these instructions you will :guitar:

---

