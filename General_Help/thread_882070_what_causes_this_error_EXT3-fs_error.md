---
title: "what causes this error? EXT3-fs error"
date: 2008-08-06
forum: General Help
---

### Post by MountainX on 2008-08-06
Trying to understand my slow disk performance. Seeing errors I don't understand.

```
[104070.269918] EXT3-fs error (device dm-6): ext3_new_block: Allocating block in system zone - blocks from 78249984, length 1
```

To identify dm-6, I did:
```

cat /sys/block/dm-6/dev
254:6

```

Then I looked here:

[/CODE]
/sys/block/dm-6$ ls -la /dev/mapper
total 0
among the entries is:
**brw-rw----  1 root disk 254,  6 2008-08-02 01:22 sdd1_crypt**
[CODE]

/dev/mapper/sdd1_crypt is ext3, 1.9T  RAID-0 on Areca 1220 using 2 Samsung HD103UJ. 

Maybe this is a compatibility problem with those drives (although I thought that only happened with RAID levels that used parity)...

**Still looking for help**!

---

### Post by MountainX on 2008-08-06
I'm also getting this error

```
[ 3642.345984] gvfsd-smb[8256] general protection rip:7ff3f099e2fc rsp:423ef5b0 error:0
```

---

