---
title: "Ubuntu 9.10 won't start after upgrade (ctrl-alt-f1 doesn't work)"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by outlikeashoe on 2009-10-19
Hi, all started updating amarok (for developing reasons): in order to update it, I had modified the apt sources.list to use the Karmic repos, and I had to update other packages, once done it and rebooted the touchpad wasn't working. I tried modifying the xorg.conf but nothing happened, then I read somewhere to try updating the ubuntu-desktop package (upgrade to 9.10).
I tried that way, but after a reboot the OS won't load.
Black screen. (also waiting half an hour)
If I type ctrl-alt-f1 it shows only:
> Starting up ...
Loading, please wait.
and nothing else.
The only key combination that works is ctrl-alt-del to reboot, saying: > Give root password for maintenance (or type Ctrl-D to Continue)
But entering the root password still reboot the system (I only have the time to type one line).

Ask me anything that should be useful to solve this issue.
I'm now using the same laptop using Vista (dual boot) with Ext2IFS driver and the Yareg tool for the home (ReiserFS).
I already tried to give a look to some log files but I cannot found nothing useful.

Thank you in advance.

---

### Post by outlikeashoe on 2009-10-21
Googling allover the net, I think that should be this issue: 

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430374](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430374)

I'll try following the instructions on that page.

---

