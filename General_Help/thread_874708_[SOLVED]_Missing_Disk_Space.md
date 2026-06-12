---
title: "[SOLVED] Missing Disk Space?"
date: 2008-07-30
forum: General Help
---

### Post by tristevoix on 2008-07-30
Hello,

How's you all?

This is a cross post from here:
[http://ubuntuforums.org/showthread.php?p=5422725#post5422725](http://ubuntuforums.org/showthread.php?p=5422725#post5422725)

Didn't get any answer after a week, so I guess I posted me question at the wrong place. Copy/pasted it here instead, hoping I'll get some answers. ^_^

Anyway, when I was using the live cd and wanted to search my hard disk, I would select the 320 gb media. However, now that I've actually installed ubuntu (Hardy Heron 8.04), things look different.

GNOME system monitor tells me (under file system) that I have 2 devices -- /dev/sda1 and gvfs-fuse-daemon. Both have total: 286 gb, free: 282 gb, available: 268 gb, used: 4 gb. [Update: I've now added another 320 gb hd for data storage: total: 295 gb, free: 295 gb, available: 280 gb, used: 191 mb. Owned by root (I think) and I can't do anything with it!)] Anyway, I don't know how to make this add up to 320. And what's the difference between free and available?

Looks like I messed something somewhere!

Thanks for your help! ^__^

---

### Post by justleen on 2008-07-30
keep in mind that ext2/3 resevere a certain % of disk space for journaling info.. so you never get the full capacity when using ext3 (ex2 uses less)

---

### Post by tristevoix on 2008-07-30
Thanks, mate! That adds to the explanation and it's much appreciated! ^_^

---

