---
title: "Locking up system"
date: 2008-09-21
forum: General Help
---

### Post by tenacity85 on 2008-09-21
Hi, I'm an Ubuntu newb, and I just encountered a problem this week. I'm running an IBM thinkpad T42. My computer locks up and the screen goes nuts, either from the boot menu or sometimes I get lucky and get into the OS before it locks. Any ideas what this could be? Any ideas as to how to fix this? Any help would be greatly appreciated!!

Sarah

---

### Post by phidia on 2008-09-21
Welcome! If you provide more of your system specs and the version of Ubuntu you are using that will help.
When your computer "locks" is it totally unresponsive? Try pressing Alt+Ctrl+F1 if that opens a commandline window you can try to login and enter "dmesg".

You can also have a look at /var/log/messages and /var/log/syslog to see if there are any notable messages there. Sometimes the System Log from the top panel System > Admin will provide info too but if your desktop isn't working then you will need to use commandline. 

One other thing to try if none of the above works boot in recovery mode.

---

### Post by tenacity85 on 2008-09-21
I'm using 8.04 . Didn't have any problems with it (or my computer in general) till now. Installed in May/April. The only thing I know is it's a Thinkpad T42 with a 60GB hitachi hard drive. I think it's got 1.8 gig of mem. 

I can't get to a point where I can access the Alt+Ctrl+F1. So, no command lines. I think my hard drive itself is shot, but I'm just so perplexed at the general craziness of the whole thing.

---

### Post by phidia on 2008-09-21
> **tenacity85 said:**
> I'm using 8.04 . Didn't have any problems with it (or my computer in general) till now. Installed in May/April. The only thing I know is it's a Thinkpad T42 with a 60GB hitachi hard drive. I think it's got 1.8 gig of mem. 

I can't get to a point where I can access the Alt+Ctrl+F1. So, no command lines. I think my hard drive itself is shot, but I'm just so perplexed at the general craziness of the whole thing.

Can you press escape and enter the grub menu (if you need to) and select recovery mode and try to boot from that?
If that doesn't work you could try a live cd-maybe you have an Ubuntu desktop/live cd?

BTW what does "the screen goes nuts" mean? Describe what you're seeing so that others get a clear representation of what is actually happening.

---

### Post by tenacity85 on 2008-09-21
I'm searching for my cd. Can't get to the grub menu. Screen goes nuts i.e. everything is locked, text/whatever is on the screen when it locks flashes, gets all scrambled, and sometimes the screen just goes blank. then the process repeats/randomizes.

---

### Post by phidia on 2008-09-22
It sounds like you need to boot from a live cd and save/back up your home directory (files you want to keep) and then reinstall or check the hard drive. There is a program called [SMART]("http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology") that can tell you if that drive is failing.

---

