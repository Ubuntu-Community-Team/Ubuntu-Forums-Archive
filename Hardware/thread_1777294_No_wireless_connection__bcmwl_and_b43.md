---
title: "No wireless connection / bcmwl and b43"
date: 2011-06-07
forum: Hardware
---

### Post by deceptor on 2011-06-07
Hi,

I'm using Ubuntu 11.04. This morning an update of bcmwl-driver (version 5.100) for my BCM4312 wireless card failed. Someone already submitted this to launchpad: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/793966](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/793966)
There is only a "fi" to much in the postprocessing script, btw.

Before I took a closer look on that problem, I tried the b43 driver. I installed the drivers with synaptic and modprobed the module by hand. The wireless connection was established immediately. But after waking up the laptop from standby, the connection cannot be established using the b43 module. I get the error message "wlan0: *deauthenticated* (*Reason*: *15*)"

Then I tried an older version (5.60) of the bcmwl-driver, fixed the ubuntu 5.100 version and also tried the 5.100 version directly from the broadcom website. And still there is no connection to my wireless network with all three driver versions. The card is active, but iwlist returns no scan results.

So, does anyone have a clue what I've messed up?

---

