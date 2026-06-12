---
title: "Multi-screen setup and Nvidia x server settings - default stopped working"
date: 2013-03-22
forum: Hardware
---

### Post by TheCadaver on 2013-03-22
This has been bothering me for quite a while now, and I haven't been able to find a solution to it myself. I have a multiple screen setup (On a Nvidia GTX 550 Ti), and, although the screens work, it stopped automatically going into dual monitor mode every time I log in. Instead, I have to manually go to the Nvidia x server settings every time, where the second monitor is disabled, and manually enable this monitor. The weird thing is, this works completely fine on the other user profiles on my system. They all automatically enter the dual monitor setup except mine.

Clicking "Save to existing x configuration file" doesn't seem to do anything. I've got no clue on how to fix this. Can anybody help?

---

### Post by papibe on 2013-03-22
Hi TheCadaver.

Several Nvidia settings are stored in ~/.nvidia-settings-rc

Make sure your file it is not owned by root. If so, remove it, and create a new one by saving your settings on the 'Nvidia X Server Settings' again. 

Let us know how it goes.
Regards.

---

