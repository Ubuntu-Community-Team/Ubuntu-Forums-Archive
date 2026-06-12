---
title: "Increasing swap?"
date: 2008-11-05
forum: General Help
---

### Post by uid313 on 2008-11-05
I installed Ubuntu using Wubi on a computer with 256 mb RAM.

The swap is too small. How do I increase the size of the swap?

---

### Post by uid313 on 2008-11-05
I think I've solved it myself.

```
swapoff /host/ubuntu/disks/swap.disk
rm /host/ubuntu/disks/swap.disk

dd if=/dev/zero of=/host/ubuntu/disks/swap.disk bs=1024 count=524288
mkswap /host/ubuntu/disks/swap.disk
swapon /host/ubuntu/disks/swap.disk
swapon -s
```
Creates a ~512 mb swap.

---

