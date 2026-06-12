---
title: "Linuxant Conexant Modem Problem"
date: 2004-11-23
forum: Hardware &amp; Laptops
---

### Post by byoon on 2004-11-23
Need a solution:

Problem:
/dev/ttySHCF0 keeps reseting to group ID root after a reboot while I need it to be in the dialout group.

Information:
I'm trying to get gnome-ppp to work as user.  Works fine as root.

I have a Conexant HCF modem. Installed Linuxant's modem driver, wvdial, and gnome-ppp. Added myself in the dip group to access pppd (and am already part of the dialout group). If I "chgrp dialout /dev/ttySHCF0", gnome-ppp works fine and I can connect with my modem. Once I reboot, the group ID for /dev/ttySHCF0 goes back to root.

I assume this has something to do with HAL or whatever Ubuntu uses to recreate the devices each time the computer boots up. Is there any way to force /dev/ttySHCF0 to be in group dialout upon bootup?  Does this have to do with userspace?

Thanks.

---

### Post by byoon on 2004-11-25
Please, how do you set thr group ID for devices configured on boot.

---

### Post by byoon on 2004-12-03
I have a solution for those who have read this post and have the same problem.  There must be a more elegant way, though.

I edited /etc/init.d/bootmisc.sh and added "chgrp dialout /dev/ttySHCF0" to the end of the file.  Now I can access the modem with a normal user who is in the dialout group.

---

### Post by az on 2004-12-04
I think the sl-modem-daemon package does this for it's device.  Something will have to be written which can do this for any winmodem....

---

