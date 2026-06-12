---
title: "Disks usage reports inaccurate/faulty?"
date: 2008-09-02
forum: General Help
---

### Post by Mr Sprout on 2008-09-02
Howdy all,

My system contains 2 1TB hard drives, one has a fresh install of Hardy on and the other is empty for now. Each disk has an actual capacity of about 930 gigs, but Ubuntu is reporting them both as far from empty. 

My ubuntu drive currently reports in with 864GB free, with only 8.4GB used.

My empty storage drive reports in with 877.4GB free, with 46.8GB used whilst containing nothing at all.

I've checked in gparted and it reports the storage drive with 7.53GB used, even though it's empty!

Neither of the reported usages on these drives make sense to me, and this kind of thing **really** bugs me. Any help you guys could offer would be much appreciated.

---

### Post by Mr Sprout on 2008-09-02
I hate to bump this, but I've been searching everywhere since posting and still found nothing that helps me.

Any ideas?

---

### Post by drs305 on 2008-09-02
> **Mr Sprout said:**
> My empty storage drive reports in with 877.4GB free, with 46.8GB used whilst containing nothing at all.


The ubuntu system automatically reserves 5% of the partition for system operations. I can't swear that it does this on non-system drives but it appears to and that would make sense since even non-system drives would be journaled. In your case that would be about 46GB (.05x930). That checks with what you report. Gparted may only look at physically available space and not take the reserved space into account.

tune2fs can change the amount/percentage of reserved disk space with the "-m" switch. Refer to the man page ( man tune2fs ).

---

### Post by Mr Sprout on 2008-09-02
> **drs305 said:**
> The ubuntu system automatically reserves 5% of the partition for system operations. I can't swear that it does this on non-system drives but it appears to and that would make sense since even non-system drives would be journaled. In your case that would be about 46GB (.05x930). That checks with what you report. Gparted may only look at physically available space and not take the reserved space into account.

tune2fs can change the amount/percentage of reserved disk space with the "-m" switch. Refer to the man page ( man tune2fs ).

Brilliant! Works a treat. 

Thanks so much.

---

