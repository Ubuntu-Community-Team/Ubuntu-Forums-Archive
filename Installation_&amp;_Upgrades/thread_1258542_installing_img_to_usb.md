---
title: "installing img to usb"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by senectus on 2009-09-05
I've just finished installing the UNR img to a brand new 4 gig usb drive and now the USB drive thinks its just under 1 gig in size?!?

Does this process somehow stop me being able to partition off the other 3 gig for standard file storage?
or even use the whole 4 gig in one partition for the same purpose?

---

### Post by dandnsmith on 2009-09-05
It's quite annoying, isn't it?
I discovered that, and also couldn't find a way to do anything with it, as it was, as it even marks the stick as total-size 1GB, which then gives nonsensical data to various partitioning tools. I couldn't even get the space by shrinking the partition, so gave up (and used a smaller capacity stick).

I suspect you'd have to do some binary editing on the basic info the drive holds about itself.

---

### Post by senectus on 2009-09-05
yeah I just this:
[https://bugs.launchpad.net/win32-image-writer/+bug/370500](https://bugs.launchpad.net/win32-image-writer/+bug/370500)

I'm not giving up on it yet... but that is pretty crap :-/

---

### Post by dandnsmith on 2009-09-06
I hadn't seen that - hadn't bothered to search once I found the problem.

The allocation of 'blame' seems a little odd - I created the thing under linux with a dd command (as recommended), so it cannot be the fault of imagewriter, which is only doing what it was told to. It is the way that the image is defined which is the problem, as it only works 'correctly' when writing from the start of the stick (and so overwriting the boot block, partition table etc).

---

