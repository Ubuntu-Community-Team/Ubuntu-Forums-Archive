---
title: "Install Issues"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by JacobHaug on 2009-04-30
[B]Problem 1

[/B]When I booted Ubuntu via the live DVD it did not see either of my two internal hard drives.

I tried running an fdisk -l, and no drives were displayed.  I checked the fstab file, and again my drives were not present.

I believe this is due to the fact that the drives were SATA hard drives.  After adding the following **pci=nomsi **to the boot param, I was then able to see my drives and get past step 5 of the installer.

See step 4 in the following tutorial for more info on pci-nomsi.

[http://www.ubuntu1501.com/2007/01/installing-ubuntu-on-your-dell-1501.html](http://www.ubuntu1501.com/2007/01/installing-ubuntu-on-your-dell-1501.html)

**Problem 2**

Now, during the install I get this error....

```

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

```I don't believe the issue is related to the DVD or my DVD drive.  It's a brand new drive, and it functions fine.  I burned it on the slowest speed twice now, still with no luck. Also, I did a disk check on the Ubuntu screen and the disk checks out.

What else could be causing this?  Please help!

[I]Side note: I have installed Ubuntu on this machine in the past with an IDE drive instead of the SATA drives....however, I need to be using the SATA drives.

Another Side Note:  Linux Experience is advanced, Ubuntu experience is basic to intermediate.
[/I]

---

