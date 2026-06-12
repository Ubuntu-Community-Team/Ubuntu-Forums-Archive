---
title: "LVM Problems After Upgrade/Reinstall"
date: 2009-03-20
forum: Hardware
---

### Post by bodnar11 on 2009-03-20
I'm having some problems with LVM and a couple of hard drives.

I had LVM set up in Ubuntu 8.04 for two hard drives acting as a file server for my network (Hardy was installed on a third, separate drive without LVM.) A couple days ago, after botching a video driver update, I decided to wipe the Hardy install and upgrade to Intrepid. The two disks, sda and sdb, were/are set as separate physical volumes making up a single volume group and logical volume.

Ever since the fresh Intrepid install, and after reinstalling LVM2 and system-config-lvm, I haven't been able to access the logical volume. The disks appear to be working, and the volume group name and logical volume name appears in the GUI as I had them before. The only difference shown is now instead of physical volumes consisting of /dev/sda and /dev/sdb, it shows /dev/sdb and /dev/block/254:1.

I'm hoping that it is just some small command I need to switch the physical volume reference back to the way it was, but I've tried searching and haven't come up with anything this far. Any help is greatly appreciated.

---

### Post by bodnar11 on 2009-03-20
Quick update. I installed testdisk from the repositories and ran it on sda and sdb. No errors appeared. I'm thinking this verifies that the disks are okay and hopeful that this can still be recovered somehow.

---

