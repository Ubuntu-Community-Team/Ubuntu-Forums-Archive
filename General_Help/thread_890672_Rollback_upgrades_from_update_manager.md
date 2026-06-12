---
title: "Rollback upgrades from update manager"
date: 2008-08-15
forum: General Help
---

### Post by jonmach on 2008-08-15
Hi all,

I've had a very healthy ubuntu 64 bit 8.04 system running for ages.  Last night I installed the recommended updates, and my network has now ceased to exist.  I can't see my router, and setting my IP address directly doesn't resolve the problem.

Is there any way to roll back upgrades?  I'm not sure which update broke the network, so reinstalling wouldn't resolve the problem, because I'd still be in a fix when the upgrade broke it again.

Any help appreciated.

Jon

---

### Post by lucamanu on 2008-09-17
Hi, I'm experiencing a similar problem since a couple of days. I did not install anything new on a Hardy 8.04 working like a perfect clock, so I guess that the problem must have been caused by some updates installed then. 
When I boot the workstation, the startup hangs up for ages, then the BusyBox command line appears. 
I can start the system choosing the recovery option, and without doing anything I select the "resume normal booting" option. Then the system starts without problems.
What log should I check to debug the problem?
Is there a way to rollback the updates?
Thanks

---

### Post by stoneage on 2008-09-17
Synaptic => File => History will tell you what was installed when.

---

### Post by lucamanu on 2008-09-17
Thanks stoneage.
Unfortunately it didn't help much because according to synaptic I did not install anything for 4 days, while I am sure that an upgrade was launched (with update manager) not more than 2 days ago. Is this possible?
:confused:

---

### Post by untitledtv on 2009-07-01
Was there a resolution to this, I had the same problem!

---

### Post by convert_mrta on 2009-07-02
Same here.  I have a related question....  I see the commit log entries for the packages.  But how do I roll one or more of them back from there.  Do I copy/paste them into the Synaptic manager, find them (it) and uninstall?

Greg

---

### Post by untitledtv on 2009-07-02
I figured it out last night, thank goodness....

Yes, you do a find -- but rather than doing uninstall, you go to packages and there's an option where you can force a change. just force the change back to the prior version.

It worked like a charm...fortunately the hardline ethernet was still working because my wireless was smoked....you need to be able to download the old packages.

I used Synaptic instead of update manager.

---

