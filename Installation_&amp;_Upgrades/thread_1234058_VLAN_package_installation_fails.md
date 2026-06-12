---
title: "VLAN package installation fails"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by klaus0009 on 2009-08-07
I have to install the vlan package on a few machines in a lab that has no internet access. I've tried 8.10 and 9.04. I see the 8021q module can be installed to the Kernel, however:
 
sudo apt-get install vlan -> package not found on both builds
 
I have ubuntu server running with a 2.6.27-7 kernel and am able to install vlan on that.
 
I copied the var/cache/apt/packages from the server onto a thumb drive and diff'd the thumb drive against my 8.10 box (which will not install vlan) and there seems to be no difference.
 
I'm confused, how can I get this package installed?
 
Thanks!

---

