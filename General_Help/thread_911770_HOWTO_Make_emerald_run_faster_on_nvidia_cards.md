---
title: "HOWTO: Make emerald run faster on nvidia cards"
date: 2008-09-06
forum: General Help
---

### Post by droazen on 2008-09-06
For the longest time I experienced user interface lag running emerald on an Nvidia GeForce 8600M GT card (in a MacBook Pro Santa Rosa) -- ESPECIALLY when switching tabs in apps like firefox. There would often be a 2-3 second delay each time I switched to a different tab in firefox with emerald running, which got annoying pretty quickly. Killing emerald and using a different window decorator solved the problem, but I missed my pretty window borders :p Searching around I found a fair number of people with similar nvidia cards who had the exact same problem, but I didn't find a solution until just now -- so I thought I'd post the solution in the hopes that it might save someone else some anguish someday!

Apparently the bug was not in emerald, but in the nvidia-glx-new driver itself. It has been fixed in the latest versions, however the nvidia-glx-new driver in the Hardy repos is a bit out-of-date and doesn't contain the fix. The easiest way to obtain the latest driver is:

```
1. sudo apt-get install envyng-gtk
2. go to the system tools menu, and start "EnvyNG"
3. click "nvidia", then select "Install the Nvidia Driver (Automatic Hardware Detection)"
4. reboot

```

After you reboot, you should no longer see any lag when switching tabs in firefox with emerald running! :D

Reference: [https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/144216/comments/39]("https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/144216/comments/39")

---

