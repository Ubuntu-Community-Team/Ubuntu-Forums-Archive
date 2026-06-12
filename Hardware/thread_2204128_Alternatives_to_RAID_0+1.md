---
title: "Alternatives to RAID 0+1"
date: 2014-02-06
forum: Hardware
---

### Post by pcman312 on 2014-02-06
Are there any alternatives to a RAID 01/10 setup that gives at least one level of hardware redundancy as well as allowing you to have more than 1X the disk space available (in a 01, if you have 4 drives of size X, it gives 2X the storage space) in a single logical drive? The solution does not have to be at the hardware level (like RAID), but could be at the OS level. If it is at the OS level, be aware that this computer would be running Windows 7 Pro x64.

---

### Post by Gone fishing on 2014-02-07
ZFS and BTRFS come to mind as alternatives to a traditional RAID system heres a few links:

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)
[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

---

### Post by pcman312 on 2014-02-09
> **Gone fishing said:**
> ZFS and BTRFS come to mind as alternatives to a traditional RAID system heres a few links:

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)
[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

Unfortunately, those don't work for Windows. I'm thinking that I won't be able to accomplish my goals in this context. I'm thinking I'll just do multiple drives on my desktop, manually managing them, but then have a separate backup system with redundancy running linux (and probably ZFS, but I need to do some more research before making that decision).

---

