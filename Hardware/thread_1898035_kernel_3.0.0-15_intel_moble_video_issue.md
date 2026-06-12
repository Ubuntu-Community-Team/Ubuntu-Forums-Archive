---
title: "kernel 3.0.0-15 intel moble video issue"
date: 2011-12-20
forum: Hardware
---

### Post by burntpuppy on 2011-12-20
Hi all;
 FYI, Dell e5510 laptop with I915 graphics. Updated to the latest kernel (3.0.0-15) and the onboard lcd ( eDP1) stopped working. reboot with 3.0.0-13 and everything is cool again.
In order to select previous kernel
edit /etc/default/grub
change the line that has;
GRUB_HIDDEN_TIMEOUT=0
to something like
GRUB_HIDDEN_TIMEOUT=10

then 
sudo update-grub

when you reboot you will have 10 seconds to chose an older kernel
HTH
Pat

---

