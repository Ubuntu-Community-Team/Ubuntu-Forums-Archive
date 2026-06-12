---
title: "MDADM cannot remove"
date: 2009-06-17
forum: Hardware
---

### Post by DoneRightI.T. on 2009-06-17
Hello Again,

I have removed my software raid 5 device by:
```
umount /dev/md0
mdadm --stop /dev/md0
mdadm --zero-superblock /dev/sdb
```

now when I do:
```
mdadm  --examine  --scan --config=mdadm.conf
```
it returns
*ARRAY /dev/md0 level=raid5 num-devices=13 UUID=d9316af6:94745fa0:b3a4010d:90c0b7b2*

I am unable to remove this device, how would I go about gathering information about this? drive details etc. so that I may completely remove it?

Second question: how would I go about altering this information so that the spare=0

Any help is appreciated.

---

