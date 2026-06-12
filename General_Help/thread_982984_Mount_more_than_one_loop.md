---
title: "Mount more than one loop"
date: 2008-11-15
forum: General Help
---

### Post by ozman30 on 2008-11-15
Ubuntu 8.0.4
Hi all i am running into a small problem i would like to mount more than one loop device as drives this is my commands and what happens. I only use CLI not GUI.

First loop device
cd /dev
sudo dd if=/dev/zero of=LoopTest0 bs=1MB count=1 seek=10000
sudo mkfs.ext3 -F /dev/LoopTest0
sudo mount /dev/LoopTest0 -t ext3 -o loop /var/LoopTest0

This makes /dev/LoopTest0 and a 10GB mounted drive


Second loop device
cd /dev
sudo dd if=/dev/zero of=LoopTest1 bs=1MB count=1 seek=10000
sudo mkfs.ext3 -F /dev/LoopTest1
sudo mount /dev/LoopTest1 -t ext3 -o loop  /var/LoopTest1

This makes /dev/LoopTest1 but i get the following error when mounting it

mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
       
So i look at the logs
[ 4454.851237] Buffer I/O error on device loop1, logical block 12
[ 4454.851271] Buffer I/O error on device loop1, logical block 13
[ 4454.851305] Buffer I/O error on device loop1, logical block 14
[ 4454.851340] Buffer I/O error on device loop1, logical block 15
[ 4454.851377] Buffer I/O error on device loop1, logical block 16
[ 4454.851411] Buffer I/O error on device loop1, logical block 17
[ 4496.647449] kjournald starting.  Commit interval 5 seconds
[ 4496.648027] EXT3 FS on loop0, internal journal
[ 4496.648040] EXT3-fs: mounted filesystem with ordered data mode.
[ 4522.927936] VFS: Can't find ext3 filesystem on dev loop1.

Any help would be greatly appreciated!

---

