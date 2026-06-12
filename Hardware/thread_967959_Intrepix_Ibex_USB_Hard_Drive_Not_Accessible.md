---
title: "Intrepix Ibex USB Hard Drive Not Accessible"
date: 2008-11-02
forum: Hardware
---

### Post by dafi on 2008-11-02
I've found the kernel has this problem [https://bugs.launchpad.net/ubuntu/+bug/279881](https://bugs.launchpad.net/ubuntu/+bug/279881) but I can't find a workaround.

This make Intrepid unusable :(

---

### Post by dafi on 2008-11-07
UP

Is it possible doesn't exist a workaround for this ridiculous regression bug?

---

### Post by timcredible on 2008-11-07
from the links you provided, it looks like the root problem is the hard drives not behaving correctly (they don't return all the data they were asked for, and don't report why they didn't return all the data, hence the sense code errors).  

maybe do a fsck on your drive and see if that helps.

---

### Post by dafi on 2008-11-07
> **timcredible said:**
> maybe do a fsck on your drive and see if that helps.

Hi thanks for your hint

The drive works fine on Gutsy and Hardy heron (both 32 bit) and it is formatted in NTFS, do you find the filesystem can be a problem?

---

### Post by dafi on 2008-11-15
If I do a manual mount all works fine so I think the problem is related to gnome automount.

Any idea?

---

