---
title: "Tor / Privoxy re-installation in Jaunty 9.04"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by slowtrain on 2009-08-14
I recently upgraded my system to 9.04, and my existing tor / privoxy installation ceased to work.  I found a way to solve this problem, which perhaps people will find helpful.  Here it is:

Basically, you need to install a version of Tor that works in Jaunty.  Problem is that your existing version of Tor cannot be easily uninstalled.  Tor has been removed from the repositories, so you can't remove the existing version with either Synaptic or a command such as sudo apt-get remove tor .  They will tell you tor isn't installed, even while tor is running in the background!

To uninstall tor, use this:

sudo dpkg --purge tor

Then, to get the new version of tor, follow the instructions here:

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

Let me know if this proved helpful.

Cheers!

---

