---
title: "HPLIP installed with syaptic, but not there!"
date: 2009-12-29
forum: Hardware
---

### Post by kmclar on 2009-12-29
Hi, hoping someone can help...  

Running 9.10 i386... installed hplip, hplip-gui, hpijs, and hpijs-ppds in synaptic package manager.  Install went normally, and synaptic shows all to be installed, yet there is no item in System > Preferences for HPLIP as there usually is, and if I try hp-toolbox in terminal, I get "command not found".

Some background... in attempt to get HP Photosmart C4780 going,  I had  installed HPLIP 3.9.12 from hplip.net, because I could not see ppd file for that printer in the list with the 3.9.8 version that came with 9.10.  Well, it turned out that was because I had not installed hpijs-ppds.  So, I uninstalled the 3.9.12 using "sudo make uninstall" then re installed all the above packages using Synaptic.

I wondering what I broke?  I have another machine also running 9.10, and after installing the packages above with Synaptic on that machine, all is perfect - HPLIP and printer work great.

Any ideas?

Thanks!

---

