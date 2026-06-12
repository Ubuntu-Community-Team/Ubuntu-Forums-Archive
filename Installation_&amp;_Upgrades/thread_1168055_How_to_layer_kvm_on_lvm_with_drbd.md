---
title: "How to layer kvm on lvm with drbd"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by joec22 on 2009-05-23
Can someone point me in the right direction for testing a kvm implementation that might provide HA?  I want to have kvm hosts that I can take snapshots on, but also provide HA.  I'm confused about how to layer the implementation.  Should it be setup like this?

kvm on top of drbd on top of lvm


or does lvm go on top of drbd?

And what type of file system should I use -GFS or ext3 or something else?

Thanks

---

### Post by hiasl on 2009-09-12
Hi,

though this post is quite old, here's my reply?

1.) Did you solve your question
2.) I'm interested in that as well: I would suggest the following 2 setups:

======= Setup A =======
2 Machines with 2 drives:
RAID1 (2 drives) > DRBD (2 machines, 2 primaries, 1 ressource) > LVM (one LV for each KVM Guest) > KVM
Problem: I doubt that LVM will manage to handle access on too of KVM from both machines.... I guess the this will lead to data inconsistency

======= Setup B =======
2 Machines with 2 drives:
RAID1 (2 drives) > LVM (one LV for each KVM Guest) > DRBD (2 machines, 1 primary, 1 ressource for each KVM Guest) > KVM
Problem: you need one DRBD ressource for each KVM Guest, so you need a lot of ports for DRBD, more configs....

What do you think?

Matthias

---

### Post by Ulexus on 2010-12-10
I use a setup similar to the last poster's "a" option:

RAID -> LVM -> DRBD -> LVM -> KVM
Each VM has its own LV, so the filesystems can (and are) each different, being localized to the VM.  The dom0 (to use Xen parlance) machine runs on the RAID, but outside the LVM stack so that bootstrapping it in case of problems is easy (straight ext4 on RAID so that any Linux boot CD/USB will be able to work with it).

Why two levels of LVM, you ask?  Why, so that I can tack on additional storage within DRBD, of course.  Both LVM and DRBD support hot extension of their sizes.  The trick to this dual-layer LVM stack is the order of operations.  LVM is loaded first (I use my distibution's normal detection for this), then DRBD (again, normal detection).  To get the second LVM layer to work, though, I add 'vgscan; vgchange -a y' to my /etc/rc.d/rc.local file... that's /etc/rc.local for Ubuntu).  That way, LVM scans for volume groups again after DRBD comes up.

Keep in mind that this only give you HA for the _storage_ backend.  You still need heartbeat to manage starting and stopping the VMs.

For networking, I use the soft switch VDE bound to a TAP interface which, in turn, is bridged to my primary eth0 interface.  This way, I don't have to manage any networking within heartbeat.

---

### Post by Mannekino on 2012-06-26
I was looking for a solution for this problem also. I put in some research and managed to get it working. I have written a tutorial to get such a setup working.

[http://www.bluejay.nl/2012/06/23/simple-manual-failover-cluster-with-drbd-lvm-and-kvm-on-ubuntu-12-04-precise-pangolin/](http://www.bluejay.nl/2012/06/23/simple-manual-failover-cluster-with-drbd-lvm-and-kvm-on-ubuntu-12-04-precise-pangolin/)

---

