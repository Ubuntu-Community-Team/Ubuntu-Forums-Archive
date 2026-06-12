---
title: "Firefox shuts down often after 9.04 upgrade"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Cold-Gin on 2009-04-28
Ubuntu version 9.04
Linux Kernel 2.6.28-11-generic
Gnome version 2.26.1
Memory 748MB

Hi. I upgraded to 9.04 over this past weekend. Whenever I go to a web site that has flash or graphics, Firefox closes down unexpectedly. An example site is Fandango. I just went to order tix for a movie a few minutes ago, and when I brought up the movie I wanted to order tix for, the browser closed down by itself. This isn't the only site that the problem occurs on.

I also ran update manager, and I saw some firefox updates, but the issue still occurred when I went back to fandango.

This is really a annoying, but I suppose it could simply be a memory issue for me. I know firefox can be a hog, but I don't have anything else running but the browser.

Any thoughts on this? Thanks.

---

### Post by oschea on 2009-05-04
I have exactly the same issue in exactly the same situation. I also just upgraded to 9.04 and it triggered Firefox to fail on practically all sites with flash. Also I have plenty of memory - 4GB so I don't think it is an issue here

---

### Post by udippel on 2009-05-04
Simply to be seconded, on x86_64 at least. Without Firefox, the system has been running (uptime) for 4 days without any hitch. Firefox tends to segfault. (You can see this when you start it from the command line. I'll attach the message when it happens next here.)
But also, the stock NVIDIA driver seems to have problems; check the forum of NVIDIA.

Uwe

---

### Post by Zymous on 2009-05-04
I'm in a very similar position (botched upgrade 8.10 to 9.04, followed by an installation of 9.04 into / with /home on another partition).

Firefox crashes when trying to play an embedded flash movie (Youtube and the BBC iPlayer are two examples).

I have an ATI card not an Nvidia card.

Addendum.
My problem was rectified by going into Synaptic and "installing" the flashplugin-non-free 
and associated programmes.

-- 
David

---

### Post by DanH42 on 2009-05-28
Same problem here.
I am using an Acer Aspire One (1.6 gHz, 1GB RAM)
Sites include:
Wikipedia
Google Cache
ubuntuforums.org home page
And various others
Although, this only happens sometimes. Other times, when I reboot, everything works great.
:confused:

---

