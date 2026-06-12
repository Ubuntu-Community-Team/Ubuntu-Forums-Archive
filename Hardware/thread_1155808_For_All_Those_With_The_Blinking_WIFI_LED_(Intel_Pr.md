---
title: "For All Those With The Blinking WIFI LED (Intel Pro 3945abg)"
date: 2009-05-11
forum: Hardware
---

### Post by RoB RuLeZ on 2009-05-11
I have been struggling with this for ages and I have finally came across a fix. I just wanted to share it with all of you that have this problem as I know what a pain in the *** it is. For the fix, all you have to do is download [this](http://rapidshare.com/files/231656372/stopblink.html) and file place it in etc/network/if-up.d. To do this you will need root privileges. So open the terminal and type: "gksudo nautilus". Then when the file is in place, run it, then reboot, and hopefully your WIFI LED won't blink anymore. Not sure if it matters but I am running Ubuntu 9.04.

---

