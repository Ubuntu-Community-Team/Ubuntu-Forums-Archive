---
title: "I broke ACPI"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by crazybilly on 2007-05-02
Before the Feisty upgrade, I was running Edgy and had troubles w/ power scaling.  So I uninstalled powernowd and installed cpufreq-ondemand (as per [this post]("http://swem.wm.edu/blogs/waynegraham/index.cfm/2006/8/17/Improving-Ubuntu-GUI-Resposiveness")).  It didn't work, so I uninstalled cpufreq and reinstalled powernowd.  

Previously, suspend and hibernate worked.  Now, they both give me a black screen with a flashing underscore cursor for a while, then kick me back to the post-screensaver login screen.

Any guesses on how to troubleshoot this?

---

### Post by crazybilly on 2007-05-02
correction:  standby seems to be working.  Hibernate, on the other hand, gives the symptoms I've described.

---

