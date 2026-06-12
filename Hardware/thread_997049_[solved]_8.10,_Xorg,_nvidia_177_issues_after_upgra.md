---
title: "[solved] 8.10, Xorg, nvidia 177 issues after upgrade"
date: 2008-11-29
forum: Hardware
---

### Post by gsgleason on 2008-11-29
Just wanted to share my issue and troubleshooting and whatnot.

    I just upgraded fom 8.04LTS to 8.10 on my thinkpad R61 with nvidia graphics and kernel 2.6.27-9-generic and Xorg 1:7.4~5ubuntu.  After upgrade, I found that my system appeared to freeze when i logged out.  
    The issue turned out to be the Xorg server.  From a fresh boot, I could start X once from single user mode, and it would start just fine.  If I killed it and restarted it, there was a huge delay, even though the xorg log didn't have anything different compared to the normal startup.
    The issue turned out to be the proprietary nvidia 177 driver, installed from System>Administration>Hardware Drivers.  Using the proprietary 173 driver or the nv community driver had no issues.  
    So, I'm currently using 173 with no issues.

---

