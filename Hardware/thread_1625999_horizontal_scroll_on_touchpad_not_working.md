---
title: "horizontal scroll on touchpad not working"
date: 2010-11-19
forum: Hardware
---

### Post by emerick7 on 2010-11-19
Upgraded to 10.10 from 10.04 yesterday. Only negative thing I'm experiencing is the horizontal scroll region is not really working. Vertical works great and has it has been. Horizontal is activated (under Mouse>Touchpad>Enable Horiztonal (Edge) Scrolling.

When I move horizontally in the region, the cursor remains in the same place. If I try it many times it does work, but it's pretty much useless.

I'm using the hp tc4200 with a synaptics touchpad.

Any help or ideas? Thanks.

---

### Post by emerick7 on 2010-12-06
Problem solved!

Here's how I solved it - went to [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad), specifically where it said: "Install the DKMS driver package provided in [https://bugs.launchpad.net/bugs/308191](https://bugs.launchpad.net/bugs/308191) (comment #115, #116). Reboot, and go to System > Preferences > Mouse > Touchpad and select "Two-finger scrolling"."

Went to that link, and downloaded/installed the deb file [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/546697](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/546697) and rebooted. Didn't change a thing in the properties.

Now it works as expected!!

Just figured I'd let anyone know in the future who ran into this problem.

---

