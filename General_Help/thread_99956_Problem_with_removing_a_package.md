---
title: "Problem with removing a package"
date: 2005-12-06
forum: General Help
---

### Post by Aramil on 2005-12-06
I did the mistake to download and try to install an RPM file...I converted it to deb with alien and tried to install it.But smth went wrong and when I open Synaptic I receive the following message

E: The package cinelerra needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

The problem is that after this message pops up I cant have access to any of my packages via Synaptic.I also can't update my system.I tried to use sudo apt-get remove--force-yes "package name" but I receive the message

Reading package lists... Done
Building dependency tree... Done
E: The package cinelerra needs to be reinstalled, but I can't find an archive for it.


What can I do?Please try to explain with details cause I pretty much a noob....

---

### Post by cstudent on 2005-12-06
If you installed the deb using "**dpkg -i *package_name***" you could try to remove it with "**dpkg -r *package_name***". Afterwards run "**sudo apt-get update**" and then try opening Synaptic.

---

