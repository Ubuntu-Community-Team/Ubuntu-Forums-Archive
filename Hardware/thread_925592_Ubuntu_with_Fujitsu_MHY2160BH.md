---
title: "Ubuntu with Fujitsu MHY2160BH"
date: 2008-09-20
forum: Hardware
---

### Post by Jackhowitzer on 2008-09-20
The last time I installed Ubuntu on my laptop, the hard drive killing bug ate up all my load cycles and killed my HDD.  This was before I read about the fixes for it.  I recently reinstalled with Hardy, and tried to do the fix.  My drive was still clicking a lot and it didn't seem like it worked.  My drive doesn't display the load cycle count when I do smartctl on it, but I was wondering if anyone else has had experience with the same HDD model and whether or not you can get it fixed with Ubuntu.  Thanks.

---

### Post by IntuitiveNipple on 2008-09-20
Possibly not a great help but with Gutsy and Hardy on a Sony Vaio with a FUJITSU MHV2200BT I've never seen any problems.

---

### Post by mugwhy on 2008-09-23
> **Jackhowitzer said:**
> The last time I installed Ubuntu on my laptop, the hard drive killing bug ate up all my load cycles and killed my HDD.  This was before I read about the fixes for it.  I recently reinstalled with Hardy, and tried to do the fix.  My drive was still clicking a lot and it didn't seem like it worked.  My drive doesn't display the load cycle count when I do smartctl on it, but I was wondering if anyone else has had experience with the same HDD model and whether or not you can get it fixed with Ubuntu.  Thanks.

I have the an SATA FUJITSU MHV2120AH laptop drive and none of the "hdparm -B 255 /dev/sda" tricks work for my drive. I have been playing with the suggestions on the [https://wiki.ubuntu.com/PowerManagement]("https://wiki.ubuntu.com/PowerManagement") page. I get several long runs, maybe five minutes with no clicking, but now it appears like the drive spins down too. When I fire up any app you can hear the drive spin up. So, clicking is reduced, but the response time of the drive is adversely affected.

---

