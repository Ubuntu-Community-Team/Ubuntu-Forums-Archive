---
title: "Can i some how run my security cam in Linux?"
date: 2015-12-23
forum: Hardware
---

### Post by sonyboyj on 2015-12-23
i  got a outdoor security cam thats connected to a (ion  video to pc ) i  use ispy on windows and i need to use a driver to get it to show in  ispy. but was wondering if i can get it to work in ubuntu.  i know about  WINE i could run ispy in it but what about the driver can i install  that in wine as well

---

### Post by Vladlenin5000 on 2015-12-23
A few comments come to mind:

Firstly, as a general rule, yes, you can manage one or multiple cams in Ubuntu. I don't use such features but the [Zoneminder]("https://zoneminder.com/") software is quite popular and often cited here and elsewhere. There are others.
Secondly, WINE is a compatibility layer that allow _some_ Windows software to run in Linux (results vary, a lot). It is NOT for drivers, NEVER for drivers.

That said, the ION Video2PC has been reported as working in Ubuntu, with some tweaks. It's powered by a widely known EMPIA EM2860 chipset (at the end of the day this is what really matters, not the brand/model). You can follow instructions in this Dutch/Flemish [video]("https://www.youtube.com/watch?v=30e-N5z51vU") (I don't understand that much of Flemish but it's easy to follow anyway). The bad news is the driver has to be compiled. Definitely NOT for newbies.

---

### Post by Bucky Ball on 2015-12-23
*Thread moved to **Hardware**.*

---

