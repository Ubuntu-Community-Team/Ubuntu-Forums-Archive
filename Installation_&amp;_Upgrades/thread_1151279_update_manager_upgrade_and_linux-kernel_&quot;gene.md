---
title: "update manager upgrade and linux-kernel &quot;generic&quot;?"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by ubuntubrian on 2009-05-06
I have gotten these as being held back if I try to upgrade my system. I'm running Jaunty and other than a couple PPA sources I don't have any weird sources so I'm not sure why I get this:

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

In Synaptic they all show as upgradeable. Versions offered are 2.6.28.12.16 from 2.6.28.11.15. I haven't tried upgrading them in Synaptic though I did a bunch of OpenOffice packages that had similar issues, ie, not upgradeable with apt or update manager but I could with Synaptic. Same with google Earth. I'm more hesitant to mess with kernel up grades and think my apt knows what it's doing!
Any ideas?

Thanks!!

---

