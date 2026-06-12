---
title: "[SOLVED] Restrictid drivers - won't download/install"
date: 2008-11-19
forum: General Help
---

### Post by TCF on 2008-11-19
I'm reposting this from yesterday as I got no response..

After updating to 8.10 I was notified that restricted drivers were available for my video card. (Nvidia 7600gt) The hardware drivers window suggests "NVIDIA accelerated graphics driver (version 177)". When I go to activate the driver a window pops up that says "downloading and installing driver.." The window closes and nothing seems to have been installed. The hardware drivers window does not recognize it as being activated. What's going on here, and what do I need to to do fix the problem? Any help would be great.

---

### Post by dabl on 2008-11-19
Follow the procedure in the second post here:

[http://kubuntuforums.net/forums/index.php?topic=3098672.msg152816#msg152816](http://kubuntuforums.net/forums/index.php?topic=3098672.msg152816#msg152816)

except for Ubuntu use "gdm" instead of "kdm".

HTH   :)

---

### Post by phidia on 2008-11-19
If you're sure that the internet connection is working-open Synaptic from System > Administration and click the "reload" icon then try again.

---

### Post by _sAm_ on 2008-11-19
Same happen to me, and the solution was to first install the driver from Synaptic(search for nvidia and pick the nvidia-glx-177 driver). Then activate the driver in System>Administration>Hardware Drivers.

---

### Post by TCF on 2008-11-19
The problem seems to have been resolved. Thanks for the help dabl.

---

