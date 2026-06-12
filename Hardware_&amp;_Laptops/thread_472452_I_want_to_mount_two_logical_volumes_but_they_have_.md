---
title: "I want to mount two logical volumes but they have the same name!"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by runesvend on 2007-06-13
Hey all

I have two hard drives connected to my Ubuntu machine that each have a logical volume that I want to mount. *vgs* gives me the following:

```
  VG         #PV #LV #SN Attr   VSize   VFree 
  VolGroup00   1   2   0 wz--n-  76.22G 32.00M
  VolGroup00   1   2   0 wz--n- 233.66G 32.00M

```

The first one resides on /dev/hdd2 and the second is on /dev/hda2. I have managed to mount the second (large) one on hda2 but how do I mount the first one when it has the same name?

*lvscan* says this:
```
  ACTIVE            '/dev/VolGroup00/LogVol00' [233.19 GB] inherit
  ACTIVE            '/dev/VolGroup00/LogVol01' [448.00 MB] inherit
```

Where the second on seems to be a swap partition (this is what I was told when trying to mount it).

Thanks in advance!

---

