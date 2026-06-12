---
title: "reiserfs problems during boot but not from LiveCD"
date: 2005-11-19
forum: General Help
---

### Post by pheitman on 2005-11-19
I don't know what to say. I have 3 raid1 partitions on the first sda and sdb. sda1/sdb1 (md0) were mounted on /boot. sda1/sdb2 (md1) are swap. sda2/sdb2 (md2) are an lvm pv. I rebooted earlier today and couldn't log in. That turned out to be a file system error (reiserfs). I ran booted with a LiveCD and ran reiserfsck and as far as I can tell that problem is corrected. Rebooted again and can't boot anymore. I get 

warning: is_tree_node: node level 0 does not match to the expected one 2
dm-0: warning: vs-5150: search_by_key: invalid format found in block 9889. Fsck?
reiserfs: dm-0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data [1 2 0x0 SD]
mount: mounting /dev/root on /root failed input/output error

As I stated, when I boot from LiveCD and run reiserfsck on the root partition (/dev/mapper/lvm-root), it now reports no errors. None of the reiserfs partitions report errors. Can anyone suggest what I do next?

Thanks in advance,

Peter

---

