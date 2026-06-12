---
title: "Screwed something up"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by MBro on 2005-07-03
Ok, I followed these instructions to get my sata drive to load on bootup
Quote:
Originally Posted by spp
I am not sure if hotplug is your problem. But if it is and you need to load it earlier, run the following command:

Code:

mv /etc/rcS.d/S40hotplug /etc/rc5.d/S34hotplug



This will execute hotplug before mountall. Not tested so I can't be sure.

SP

But when i did it, i log in and my mouse isn't even lit up, I can type on the keyboard however. So inorder to fix this, should i login in into a terminal and then run

Code:

mv /etc/rc5.d/S34hotplug /etc/rcS.d/S40hotplug



To switch back what I did since all mv is is move?

---

