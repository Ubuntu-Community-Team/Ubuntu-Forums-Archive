---
title: "1 SSD vs 2 SSD Raid 0 Config.  Is it worth it?"
date: 2010-12-30
forum: Hardware
---

### Post by Marty4344 on 2010-12-30
I recently purchased 2 40GB Intel SSD's and planned on putting them in a raid configuration, however im wondering if skim is supported in Ubuntu 10.04 using raid.  

Should I go through with raid 0 (striping) on 2 SSD's?  Will I see an advantage over using just one ssd?  Also as for Data Loss ill backup the system to a 10 TB Raid 5 array.

I plan on using linux's raid and not the bios raid.

Any input would be great as I have the system basically sitting here ready to rock =)

---

### Post by psusi on 2010-12-30
You mean TRIM?  No, I don't believe it is yet.  Of course you will see an advantage, that is kind of the point of raid0.

---

### Post by Marty4344 on 2010-12-30
Yeah Trim, my mistake there.

Also just wondering if there is a considerable difference performance wise.

---

### Post by psusi on 2010-12-30
Twice the drives = twice the throughput, in theory.  Of course an SSD is already so fast you aren't spending much time waiting for it on a typical desktop anyhow, so you probably won't be able to notice much difference.

---

