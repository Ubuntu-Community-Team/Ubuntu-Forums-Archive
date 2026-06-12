---
title: "Help installing INtrepid onto SAS Drive"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by Leo.F on 2009-01-02
I've been trying to install Intrepid onto a Fujitsu MBA3300 MBA3147RC 147GB 15000 RPM 16MB Cache SAS Hard Drive connected to the SAS (Serial Attached SCSI) port on an ASUS P6T Deluxe Motherboard (Core i7)

The drive is not recognized by the partitioner so it's not possible to install Ubuntu to that Drive. Have tried Live CD x64 and Alternate CD x64 installs to no avail.

This seems to be an issue with the Linux Kernel as described in this bug report:

[https://bugzilla.redhat.com/show_bug.cgi?id=474482](https://bugzilla.redhat.com/show_bug.cgi?id=474482)

A solution has been presented:

"...There are some problems using the sas drive however because rc.sysinit and/or
the init script in the initrd try to use it before the mvsas driver has
finished making the device appear. This means that partitions on it may fail to
fsck or logical volumes fail to appear during rc.sysinit, depending on the
timing.

To fix this, what I needed to do was add a delay loop into rc.sysinit. In my
case I just hacked a loop waiting for /dev/sdc to appear just before rc.sysinit
does the "lvm vgchange -a y" to set up the logical volumes. This works fine.

To make the sas drive usable as the root file system we need a similar delay
for the device to appear before init tries to mount it as the new root,
otherwise the mount fails and the system will not boot. mkinitrd already has a
list of drivers for which it turns on a "wait_for_scsi" loop in init, but mvsas
isn't on the list. I added mvsas to the list, created a new initrd and now / is
fine on the sas drive. I have not tried /boot on the sas drive yet. ..."

And might have been fixed for the 2.6.28 release of the Kernel as per this post from the Linux Kernel Archive:

[http://lkml.indiana.edu/hypermail/li...2.2/02255.html](http://lkml.indiana.edu/hypermail/li...2.2/02255.html)

The above reports reference a Seagate Hard Drive, but since I'm also getting the same problem with a Fujitsu Drive, it must be the SAS port controller.

I've taken a look at Wubi, but since the drive is not recognized by the kernel during install, but I'm uncertain as if it'll boot from the SAS drive after transferring the Wubi install to it's own partition.

Question: Is there a way to apply the above fix for Intrepid? This would have to be done for the Installer CD as the drive is not recognized. And if it can, what would be the steps required?

I'll very much appreciate basic instructions as this will be my first time messing with install CDs for Linux.

I'm going to download Jaunty Alpha 2 just to try if the patch for 2.6.28 now recognizes the drive at install. Unfortunately there are still bugs with the nVidia drivers that would prevent me from using Jaunty full time from now on.

Thanks in advance for your cooperation and a Happy, Healthy and Prosperous New Year to all.

---

### Post by Leo.F on 2009-01-07
Tried Ubuntu 9.04 Alpha 2 and still the SAS Drive is not recognized.

Does anyone has any suggestions? I'll really appreciate it.

Be Well!

---

### Post by weaktight on 2009-02-26
I'm in the same boat here.  Did you make any progress with this?

I haven't found an OS that supports SAS on the install disk yet.

---

### Post by Leo.F on 2009-02-26
Hi weaktight, tried Ubuntu 9.04 Alpha **4** and still the SAS Drive is not recognized.

snorkius reported here that the latest Fedora recognizes the SAS drive:

[http://ubuntuforums.org/showthread.php?t=995231&highlight=core+i7+sas&page=3](http://ubuntuforums.org/showthread.php?t=995231&highlight=core+i7+sas&page=3)

I haven't tried Fedora yet, but I might be forced to do so (or any other distro that recognizes the SAS on install) in case Jaunty final still doesn't recognize it. I would hate having to leave Ubuntu due to unsupported hardware.

Does anyone know how to bring this issue to the attention of the Jaunty developers?

Please post back your findings.

Be Well.

---

### Post by weaktight on 2009-02-26
That's unfortunate.  Fedora is actually the distro I'm most used to.  I'll try that out tonight.

---

