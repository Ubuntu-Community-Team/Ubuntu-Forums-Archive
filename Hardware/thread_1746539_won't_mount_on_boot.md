---
title: "won't mount on boot"
date: 2011-05-01
forum: Hardware
---

### Post by bonfire89 on 2011-05-01
Hi there, I just started having an issue with one of my drives, it wont mount on boot, but if I skip over the error I am able to manually mount the drive.

Here is the error

```
Mount: wrong fs typs, bad option, bad superblcok on /dev/sdd1/ missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so

mountall: mount /mnt/autoMounted/sdd1 [742] terminated with status 32
mountall: Filesystem coult not be mounted: /mnt/autoMounted/sdd1
init: unreadahead-other in main process (745) terminated with status 4. An error occured while mounting /mnt/autoMounted/sdd1 
Press S to skip mounting or M for manual recover
```


Also

```
e2fsck /dev/sdd1 -f
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdd1: 356146/122101760 files (4.5% non-contiguous), 288333482/488378000 blocks
```

Any tips?

---

### Post by bonfire89 on 2011-05-04
maybe I could some how offload the data and reformat it? maybe something got corrupt?


EDIT: Never did figure this out, I ended up offloading the data and reformatting. Issue is resolved. But I will not mark it as solved since that isn't a proper answer.

---

