---
title: "[SOLVED] Ubuntu 8.10 - where is cupsys?"
date: 2008-11-11
forum: General Help
---

### Post by VictorR on 2008-11-11
After upgrade from 8.04 to 8.10 Intrepid I found that cannot print any more. Some investigation has shown that "cups" is not amongst running daemons, and /etc/init.d/cups is a broken link to non-exiting /etc/init.d/cupsys.

I searched for file "cupsys" in the installed packages, but none of them contains it. In one of the threads I read the suggestion to copy cupsys from a live CD, but I don't have one, as I did on-line upgrade.

Any ideas, how to get printing working?

---

### Post by VictorR on 2008-11-18
All my attempts to recover printing ended up with no running CUPS daemon, until I noticed, that /etc/init.d/ contained a suspicious file called cups.dpkg-new. It looked pretty much like a script to start cups, so I deleted old broken /etc/init.d/cups and renamed "cups.dpkg-new" to "cups".
"sudo /etc/init.d/cups start" launched cups successfully, all my printers came back to Print dialog.

---

### Post by dazzlindonna on 2009-01-01
I could almost cry that I finally found this thread.  I've been struggling with this problem all day, after upgrading to 8.10 from 8.04.  What a simple solution to a hair-pulling problem.  Thank you.

LATER:

/sigh....All was well for a few hours.  And then, cups got updated by the manager, and then, my printer disappeared again.  However, I just started the service again with "sudo /etc/init.d/cups start" and it came back.  I wonder how many times I'll have to do that.

---

### Post by AnRkey on 2009-05-03
> **dazzlindonna said:**
> I could almost cry that I finally found this thread.  I've been struggling with this problem all day, after upgrading to 8.10 from 8.04.  What a simple solution to a hair-pulling problem.  Thank you.

LATER:

/sigh....All was well for a few hours.  And then, cups got updated by the manager, and then, my printer disappeared again.  However, I just started the service again with "sudo /etc/init.d/cups start" and it came back.  I wonder how many times I'll have to do that.

Set this service to autostart...

Click System > Administration > Services
Make sure that Printer Services has a check in the box to enable it.

It should start at boot from now on. You might have to "unlock" the Services window to be able to enable the service. You need sudo admin rights for this.

R

---

