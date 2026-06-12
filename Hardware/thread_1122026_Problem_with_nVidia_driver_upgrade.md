---
title: "Problem with nVidia driver upgrade"
date: 2009-04-10
forum: Hardware
---

### Post by rodney757 on 2009-04-10
I had the nVidia driver version 177 installed and my computer was working fine. Last night I updated to version 180 and I thought everything was working. When I rebooted the computer I got a message saying image resume not found, and the it said that the nVidia kernel module was not installed. I had to use the default setting to log on. I tried activating the driver from hardware drivers. It downloaded the driver but didn't activate. I tried it with versions 177 and 180 but no luck. Any idea of what the problem might be? Thanks

---

### Post by ticket on 2009-04-10
There are two ways to install the driver - use the installer provided by nvidia, or use the deb package provided by Ubuntu.  The two methods are not compatible. If using the nvidia installer, you need to follow the nvidia instructions on the nvidia site,starting with the cleaning instructions [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)  and then trip over to [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+180+drivers](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+180+drivers)

But if you are using the Ubuntu / debian package approach (much cleaner, but less able to keep up with new nvidia releases) then the package installer should just work!

If it's any consolation, I am trying to install the 180.44 driver using the nvidia installer on Intrepid 8.1, PCI 6200 and failing the same way (driver builds, but fails to initialise on reboot).

---

