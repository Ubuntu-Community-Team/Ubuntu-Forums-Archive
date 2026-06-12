---
title: "/dev/ttySHCF0 group id resets modem permission denied"
date: 2004-11-22
forum: Hardware &amp; Laptops
---

### Post by byoon on 2004-11-22
Need a solution:

Problem:
/dev/ttySHCF0 keeps reseting to group ID root after a reboot while I need it to be in the dialout group.

Information:
I have a Conexant HCF modem.  Installed Linuxant's modem driver, wvdial, and gnome-ppp.  Added myself in the dip group to access pppd (and am already part of the dialout group).  If I "chgrp dialout /dev/ttySHCF0", gnome-ppp works fine and I can connect with my modem.  Once I reboot, the group ID for /dev/ttySHCF0 goes back to root.

I assume this has something to do with HAL or whatever Ubuntu uses to recreate the devices each time the computer boots up.  Is there any way to force /dev/ttySHCF0 to be in group dialout?  Does this have to do with userspace?

Thanks.

---

