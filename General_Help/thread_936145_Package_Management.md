---
title: "Package Management"
date: 2008-10-02
forum: General Help
---

### Post by SteelWo1f on 2008-10-02
Hi

I am having some serious design issues. I need a way to do package management and configuration management. Im going to leave the config for later, but if you have any suggestions on that can you please let me know. 

My current problem is I'm trying to set up a system for doing package management of a large number of servers. I would like to just use as many Ubuntu packages as I can. I also need build and maintain custom packages for in-house build applications. Additionally, I may need mutltiple versions of a package on the system at once. 

For example, perl, and an ithreaded perl. My problem is how can I create a new perl package that installs into /opt/pkgs that doesn't conflict with the existing one. For all my custom apps I would like to install them into /opt/pkgs/program_name/version. The perl problem is complicated even more by the management of the cpan modules.

But then how do I install a new version of a package and leave the old version installed as well. Say I have /opt/pkgs/pcap/0.9.5 and I now want to upgrade pcap. So in addition to having the 0.9.5 one lying around I will also have /opt/pkgs/pcap/0.9.8.

Basically I just need serious help with how to do package management that allows for Ubuntu packages, custom packages, and multiple versions of either.

Any ideas are greatly appreciated

Thanks

---

