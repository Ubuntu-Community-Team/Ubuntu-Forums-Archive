---
title: "Succesful distribution upgrade or not?"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by ionice on 2009-04-22
I decided to upgrade my ubuntu installation from 8.10 to 9.04 but since I ran short of time I had to shut down the computer while it was updating the system. Update Manager said that it would be ready in approximately 1 hour when I interrupted it. When I rebooted I did dpkg --configure -a and while it had crunched away for a while it started to ask questions and because I had to leave it for a while I terminated the process and launced it again with the -y option. The process finished in few minutes and installed a few packages. Because it took so little time I was conviced that my system wasn't properly upgraded so I did apt-get update && apt-get upgrade which told me the system was up-to-date. Finally I did apt-get dist-upgrade with the same result.

I cannot believe that the system can upgrade itself in just a few minutes when it said it would take an hour to complete when I first interrupted it. sources.list says I'm using jaunty repos, but how can I know that every package is really updated or am I just running a hybrid Interpid/Jaunty installation?

---

### Post by lemming465 on 2009-04-23
A lot depends on the speed of the computer, filesystem, disk, internet connection, and mirrors.  Estimates of how long it will take to download stuff can be wildly inaccurate.  Once /var/apt/cache has all the new .deb packages, applying them can be fairly quick, say 10 minutes, on a fast machine with a small number of packages (<800).  On a slow machine with lots of extras it could take 90+ minutes to apply the changes.

If any of apt-get, aptitude, or synaptic think you are fully upgraded, I'd believe them.

---

### Post by markitoxs on 2009-04-23
Updated perfectly for me, no issues at all during the process. Although it asked me about lilo configuration file. 

Best upgrade I have  ever experienced.

Internal Mic works now for me, that is really amazing, however I dont get sound through my internal speakers (headphones work fine).

---

