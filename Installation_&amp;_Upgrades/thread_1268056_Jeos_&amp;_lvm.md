---
title: "Jeos &amp; lvm?"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by texaganian on 2009-09-16
Does the current JEOS support LVM?

When I try to build a JEOS virtual machine (under ESX) it seems like it supports LVM but I'm not able to build the disk configuration I want.

What I want, I think, it pretty simple. I have to vmdk file and hence two "physical" drives. I want swap on one. On the other I want a 100MB primary partition (not in LVM) mounted as root and the rest under LVM mounted as /.

Creating the swap on sdb is simple. As is creating the /boot partition on sda.

But no matter what I do using the JEOS installer, I can't end up with a logical volume mounted as /. I can create a volume group and then the logical volume, but nowhere does it allow me to set the mount point for the logical volume.

And if I select the logical volume to edit it, it says I can't because it is part of an LVM volume group.

Am I overlooking something obvious here or am I just trying to do something that isn't supported in JEOS?

---

