---
title: "ATI Drivers not successful (9.10)"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by foldor on 2009-10-16
I have installed the beta of 9.10 and sure enough I've had an issue.

I had things working alright and didn't really ave any problems, until I got "smart" and tried to install the proprietary ATI binary driver. My video card is a radeon X1400 Mobility in a Thinkpad T60 if that helps.

I've installed it from the official repository, and it says that it is successful, but when I try to the Catalyst Control Center it says it cannot detect the drivers. Worse than that, when i restarted, it does not seem to have been successful. I still see my desktop and my laptop is still able to be used, but it wont run any compiz effects anymore, and I haven't been able to figure out how to get things back to the way they were before either.

I uninstalled the ATI drivers, and tried reinstalling, but it doesn't seem to work. I even tried installing EnvyNG and for some reason I can't even get it to run. I click it's icon but nothing ever happens.

Other than this problem though I am completely satisfied with this product. My hat goes off to all the community and the developers who make this all possible.

---

### Post by vildanovak on 2009-10-17
Hi, try [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
to get some hints. you maybe need to cleanly reinstall some packages.

---

### Post by Mark Phelps on 2009-10-17
> **foldor said:**
> I have installed the beta of 9.10 and sure enough I've had an issue.

Somewhere along the line, folks have started an ugly rumour about 9.10 having improved ATI drivers, as in restricted drivers -- which I can confirm is NOT true.

Sorry you got burned by this, but AMD is being consistent in NOT providing restricted drivers for legacy cards since they dropped them with Catalyst 9.4.  They even put out a Catalyst 9.8 recently, but I tested that and found no difference with Catalyst 9.3.

---

