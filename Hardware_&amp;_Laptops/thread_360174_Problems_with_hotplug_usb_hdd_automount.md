---
title: "Problems with hotplug usb hdd automount"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by Unconscious on 2007-02-12
I've had a 300gb seagate usb hdd attached to my edgy desktop for quite a while. When the system comes up, the seagate automounts without a problem.

A coupla weeks ago I bought another 300gb seagate usb hdd. Same basic model, a slightly newer version. This one does not automount correctly. It mounts as readonly. 

When I first got it, it worked ok, but differently than the first one. It mounted as SEA_DISK rather than usbdisk. At that time I formatted, and partitioned it (as one big one) using mkfs.ext3fs. I then backed up everything on the older disk to the new disk, using rsync. 

When I recently rebooted after a kernel update, the second hdd will only mount as readonly. Oh, and all the stuff I backed up onto it... that's all gone.

Where and how is hotplug automounting controlled from?

Anybody else having these sorts of problems?

---

