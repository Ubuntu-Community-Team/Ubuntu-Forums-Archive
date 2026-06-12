---
title: "Fsck on usb external drives ?"
date: 2013-05-09
forum: Hardware
---

### Post by cogset on 2013-05-09
I have a couple of external drives formatted to ext4,after some use I can see this message```
 EXT4-fs (sdc1): warning: maximal mount count reached, running e2fsck is recommended
``` every time I attach one of them:do I have to run a manual fsck after unmounting it,or can I safely ignore the warning ? 
Being an external drive,it obviously gets mounted/unmounted kinda frequently,so theorically I'll have to run this check pretty often.

The other one is actually worse,it's a 3.5" WD drive with its own power supply,and lately it occasionally doesn't get auto-mounted when I plug it in,the message in syslog looks like this  ```
 ubuntu-kernel: [ 3618.190700] EXT4-fs (sdd2): error count: 8
 ubuntu-kernel: [ 3618.190705] EXT4-fs (sdc2): initial error at 1366215273: __ext4_get_inode_loc:4814: inode 11143320: block 44564649
 ubuntu-kernel: [ 3618.190711] EXT4-fs (sdc2): last error at 1366215527: __ext4_get_inode_loc:4814: inode 9836246: block 39321997
```
does this mean that there is some actual filesystem damage on this drive,or can it be a sketchy power adapter,as I've read somewhere?

---

### Post by ahallubuntu on 2013-05-09
~

---

### Post by cogset on 2013-05-10
Thanks,that will take care of the first message I suppose (the disk is new and there would be no point in checking it so often),but what does the second message actually mean ?

This other disk is not so new and that line
```

EXT4-fs (sdd2): error count: 8
``` has got me worrying:can that be actual filesytem damage on that partition,and what am I supposed to do about it ?

Is **fsck -f** going to fix this ?

---

