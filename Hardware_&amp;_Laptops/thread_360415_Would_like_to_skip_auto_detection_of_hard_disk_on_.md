---
title: "Would like to skip auto detection of hard disk on boot"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by apau9786237 on 2007-02-13
Have a dual boot system with a primary hard disk on hda and two additional drives on a CMD649 IDE Raid (FakeRaid) controller. These additional disks are detected as hdg and hdh. They are configured as a RAID 0 stripped set through the Windows system, but are not needed in the Ubuntu system.

At present, Ubuntu system detects these drives on boot up, and sees the ntfs partition on one of the drives, but the partiton parameters are larger  than the drive (since it stretches over on to the second drive). This seems to cause lots of head-aches and fills the system log with un-necessary crud. It also causes the boot process to hang while it tries for several minuts to read non-existant sectors.

I would like the Ubuntu system to simply ignore these drives, since I don't need to access them anyway. I have seen lots of posts about forcing hardware detection, but can't find anything on forcing it NOT to detect.

One idea I had was to force it to not load the cmd64x kernel module, but again, I don't actually know how to do this.

Any suggestions would be greatly appreciated. Thanks.

---

### Post by apau9786237 on 2007-02-14
Have worked out the skipping of the drive. Just needed to add some boot options to the GRUB configuration... hdg=noprobe hdh=noprobe.

There are some other more detailed posts in these forums about the original problem of the drive seeking beyond its limit, and the author of these has even written a kernel patch to fix the issue. If you want more info, search for a post titled "Kernel Bug during IDE / hd probing" by IntuitiveNipple.

Regards...

---

