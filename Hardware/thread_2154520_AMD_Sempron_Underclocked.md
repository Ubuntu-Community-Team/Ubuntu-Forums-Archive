---
title: "AMD Sempron Underclocked"
date: 2013-06-14
forum: Hardware
---

### Post by oyoeli on 2013-06-14
Just installed Lubuntu on an old machine as an attempt to make it usable again.
As I understand it, Lubuntu is meant to be light on resources and therefor, quicker on older computers.

System is running quick, however, applications and plug ins are slow and unresponsive.  For example, Chromium doesn't run too quickly, and Flash is completely jumpy on it.
I ran cat /proc/cpuinfo just to see what came up, and the CPU MHz is 800.  I know that this is a 2 GHz machine.

I want to use this computer as a basic internet box.  Gmail, Facebook, YouTube, Pandora, Wordpress, etc.  These things don't require a beast of a machine, and should run just fine on this Sempron.  I hate to admit it, but Lubuntu is actually running these sites slower than Windows was.  Let's fix that...

Any ideas?  Can I somehow overclock the CPU to run at the 2 GHz it was running at before?  Should I just use a different browser?  Maybe I should just chuck the whole idea out and go all Office Space on the computer?  Open to suggestions.

Thanks,
OY

---

### Post by Yellow Pasque on 2013-06-15
800 MHz is the correct speed at idle (it automatically downclocks to cut power/heat). Try checking cpuinfo when watching a Flash video.

> Flash is completely jumpy on it
Flash video takes a strong CPU. A single core Sempron isn't going to cut it. There are alternatives like minitube, though.

---

