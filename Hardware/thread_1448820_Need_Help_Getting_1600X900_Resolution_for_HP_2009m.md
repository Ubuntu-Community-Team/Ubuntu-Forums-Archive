---
title: "Need Help Getting 1600X900 Resolution for HP 2009m"
date: 2010-04-07
forum: Hardware
---

### Post by giddyup306 on 2010-04-07
Hello all,

I got a HP 2009m monitor (for free).  It seems like the highest resolution that I can set it to is 1280X1024.  I do have a Nvidia card with the proper driver.  I did some quick searches and it looks like some cards may not support this high of a resolution.  How do I know if mine can or cannot support it?  Or is there software out there for me to get to the proper resolution?


Thanks,

Mike

---

### Post by giddyup306 on 2010-04-07
I somehow got my resolution correct.  I went browsing around the forums looking for someone with a somewhat similar issue hoping that something would work (I usually end up getting myself into trouble by doing that and installing a bunch of things I can't use).  I had the driver for Nvidia installed, but when I upgraded to 9.10 it must have deleted it somehow.  I then re-installed it, and nothing.  Then someone said to try gksudo nvidia-xconfig and after that I restarted.  I'm not sure what it was that actually fixed it, but now it automatically adjusted it to 1600X900 (upon restart).

---

