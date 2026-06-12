---
title: "iam using live cd rightnow..need help"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by ultratek on 2008-12-11
it says failed to create ext3 filesystem on sda5 or (partition f: i created through vista by shrinking main volume and partioning the left over unallocated space)

---

### Post by prshah on 2008-12-11
> **ultratek said:**
> it says failed to create ext3 filesystem on sda5 or (partition f: i created through vista by shrinking main volume and partioning the left over unallocated space)

If you are installing via live CD (native install, not wubi [within windows] install) then you should not create any "drive" or partition; leave the space as unallocated, and then, when installing, use the unallocated space to install Ubuntu.

If you've already created the partition, but now want to delete it, run the partition editor System-Administration-Partition Editor), right click the sda5 entry, and choose unmount. Then right click it again, and choose Delete. Then click the Apply button on the top toolbar.

Now, when installing, choose the "use unallocated space" option.

---

### Post by ultratek on 2008-12-11
yea ty... i had to do that... then let it set the partition as logical and not primary

---

