---
title: "Intel 947 Express Chipset - Intel Duo Core slow as molasses in January"
date: 2009-04-03
forum: Hardware
---

### Post by DJonsson2008 on 2009-04-03
I'm moving this over from the topic is Ubuntu Sluggish topic raging
elsewhere for several days. 

The answer is an emphatic YES Ubuntu Hardy Heron
is slower than it should be.

Now I'm hoping to move towards some kind of solution or understanding
why this may be on what should be a workhorse setup...
MB = Gigabyte GA 946GMX S2
CPU = INTEL DUO-CORE 1.8 GHZ
RAM = 1 GIG
HD = Seagate 80 gig 8MB cache 

Here are some generic fixes that have been applied already

_These minor config modifications...
* vm.swappiness=0 in sysctl.conf
* CONCURRENCY=shell in /etc/init.d/rc
* Services have been trimmed to a minimum.
* Orphan repositories have been removed using app gtkorphan
* Fasterfox has been used to attempt speeding Firefox.

Things improved slightly, but still I'm suprised the system does not run faster. For example even now trying to open a file with Gedit from Gnome or any other file browser takes about 30 seconds. I use the machine mostly for python programming.

I'm curious if perhaps I' don't have the right driver set for

* Intel 947 Express Chipset system wihth ICH7 southbridge?
* Built in integrated Intel Grapics accelerator 3000?

My first priority now is eliminate any possibility of the video and MB drivers being part of the sluggish slowness scenario, and then follow through with looking into any other logical bottlenecks.

How do I determine if the correct/best drivers are
is in place for this chipset?

---

### Post by DJonsson2008 on 2009-04-04
Not much action on this topic. 

Here is what I'm doing -

*  I put an order in for a Nvidia 8300GS card, about 40$ 
   and puts me into a better line of support from the 
   Ubuntu and MFG in regards to drivers and settings. 
   As well it frees up the resources the onboard GMA
   chip eats up. The gigabyte NX84S512HP will PCI-E
   will add another 512 megs to the mix.

* I'm using a program called "preload" to use my excess ram
  for caching regularly used programs.

* I've ordered a Dual set of Kingston RAM to give this 
  machine 2 gigs of Dual and instead of 1 Gig of single
  DDR about 30$

Already preload (in the Ubuntu repostory has been a big help
Read about it here...
[http://www.ubuntu-unleashed.com/2008/03/tweak-ubuntu-boot-speed-and-application.html](http://www.ubuntu-unleashed.com/2008/03/tweak-ubuntu-boot-speed-and-application.html)

---

### Post by DJonsson2008 on 2009-04-06
The Nvidia PCI-E card arrived and made a vast difference in the performance of this unit. I've since though developed an interest in Xbuntu but now with both Ubuntu and Xbuntu loaded on the same HD, can move between the 2 as appropriate.

Perhaps someone could tweak the intel drivers and jockey-gtk (AKA Hardware drivers) and displayconfig.gtk GUI's to get better response with the onboard video but you can read here in this wiki the Intel GMA has a weakness in how impacts resources.

[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

For 40$, this made a big difference.

---

