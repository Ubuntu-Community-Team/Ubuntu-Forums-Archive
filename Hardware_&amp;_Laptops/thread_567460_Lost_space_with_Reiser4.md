---
title: "Lost space with Reiser4"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by emil.s on 2007-10-04
```
root@servern: /etc/skel # mkfs.reiserfs /dev/hdd1
mkfs.reiserfs 3.6.19 (2003 www.namesys.com)
...
...
...
ReiserFS is successfully created on /dev/hdd1.
root@servern: /etc/skel # mount /dev/hdd1 /mnt
root@servern: /etc/skel # df 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdd1             20043416     32840  20010576   1% /mnt
root@servern: /etc/skel # umount /mnt
root@servern: /etc/skel # mkfs.reiser4 /dev/hdd1
mkfs.reiser4 1.0.6
...
...
...
Creating reiser4 on /dev/hdd1 ... done                                                                                                    
root@servern: /etc/skel # mount /dev/hdd1 /mnt
root@servern: /etc/skel # df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdd1             19045748       756  19044992   1% /mnt
```

WTF!? I thought it only was Ext3 which reserved space... Or?
How do i get my "lost" bytes? :P

---

### Post by emil.s on 2007-10-10
*bump*

---

### Post by tgalati4 on 2007-10-10
All file systems occupy space.  I don't understand your question.  Are you trying to recover 1% of the disk that is in use?

I'm not sure what the difference is between reiserfs and reiserfs4 in terms of functionality.  I do know that reiserfs has some built-in indexing and that takes space.  It has a more-complete journaling system and that would probably require more space than ext3.

If you want to maximize space for media storage, then just use ext2.  Little (or no) performance loss for simple file serving.

---

### Post by emil.s on 2007-10-11
> **tgalati4 said:**
> All file systems occupy space.  I don't understand your question.  Are you trying to recover 1% of the disk that is in use?

I'm not sure what the difference is between reiserfs and reiserfs4 in terms of functionality.  I do know that reiserfs has some built-in indexing and that takes space.  It has a more-complete journaling system and that would probably require more space than ext3.

If you want to maximize space for media storage, then just use ext2.  Little (or no) performance loss for simple file serving.

The problem is that it's a lot of space on bigger volumes. 20GB is missing on a 450GB partition... (compared with ReiserFS (3.6))

---

