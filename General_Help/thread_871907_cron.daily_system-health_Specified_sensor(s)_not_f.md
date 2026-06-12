---
title: "cron.daily system-health: Specified sensor(s) not found!"
date: 2008-07-27
forum: General Help
---

### Post by JasonWalton on 2008-07-27
Every night I get a nice email drom /etc/cron.daily/system-health, which says:

  Specified sensor(s) not found!

Looking in the man page for system-health, I see it is related to "lm-sensors" and there's a see-also for "sensors", so I try running "sensors" and I get a dump of all my voltages and temperatures.  I've tried "sensors-detect", as well, although this doesn't seem to help.

I had this same problem on my old server with Gutsy, and I fixed it by removing the "-s" option to system-health, but there has to be a better way!  Where does system-health pull it's "specified sensors" from?

---

### Post by pkloves on 2008-09-27
I know it's been awhile since this was originally asked, but I thought I would reply in case anyone else is trying to figure out why they are getting this error.  It appears that the system-health tool in /usr/bin is hard-coded to look for a specific chipset in this line:

$sensorChips = "lm79-isa-*";

I just changed it to my chipset instead and it works as expected.  You can simply set the variable to "" and it works that way as well.

Strange that it would have a specific chipset hardcoded into the script...

---

