---
title: "RAID and encrypted LVM"
date: 2010-03-02
forum: Hardware
---

### Post by Fafler on 2010-03-02
I have just ordered 3 1.5 tb drives for my home server. I want to use them as one large data partition in RAID 5 with encrypted LVM, but i'm unsure how to do that. Is it RAID layer first and LVM on top of that? Or the other way around? I want to be able to add more drives to the RAID and rebuild it later as i'm going to need more space. Is that still possible with encrypted LVM on top? Anything else i should know before i put all my data into the new drives?

EDIT: The OS is placed on another drive, this is only for data.

---

### Post by Fafler on 2010-03-03
Looking around, it seems i could just create the array, put luks on it and have the filesystem directly on top of that, leaving LVM out all together. Is this presumption correct?

The drives i have ordered are from Western Digital and uses the new 4 kb format. Should i set the stripe size of the array to match?

---

