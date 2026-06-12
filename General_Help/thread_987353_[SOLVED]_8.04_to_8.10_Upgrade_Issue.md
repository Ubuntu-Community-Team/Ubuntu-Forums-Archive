---
title: "[SOLVED] 8.04 to 8.10 Upgrade Issue"
date: 2008-11-19
forum: General Help
---

### Post by SpikoPath on 2008-11-19
I currently have a Sun Ultra 60 running Ubuntu 8.04 with xubuntu-desktop, the update manager suggests an upgrade to 8.10 and when I come to go through the upgrade process it fails because there isn't enough space on the boot partition to continue. 

The partion Manager won't allow me to increase it size and it won't allow me to unmount system partitions.

My question is this, is there a way for me to boot of of a cd that has a partion manager and icrease its size and still make it bootable?

A reinstall to 8,10 is not an option as I have 7 hard drives in an lvm raid setup, the main OS is installed on the first drive which isn't part of the lvm raid setup. I have put a lot of work into getting it set up the way it is and I don't want to undo that work. I initially started with ubuntu 7.04 and have been upgrading from that point onwards.

---

### Post by SpikoPath on 2008-12-02
Although I didn't find a way to increase the boot partition, after loading the synaptic package manager, I looked at installed kernels and had lots of previous version of which I removed. space was created and issue was resolved.

---

### Post by dai_vernon on 2008-12-04
Standard desktop CDs for most distros contain some sort of partition editor to change partition sizes.  You can't touch partitions you haver mounted, and you can't unmount the partition you've booted from.  I don't know how prevalent desktop CDs for SPARC architectures are but give that a try.

---

