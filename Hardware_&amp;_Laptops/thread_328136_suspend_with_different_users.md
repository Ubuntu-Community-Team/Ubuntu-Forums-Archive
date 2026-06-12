---
title: "suspend with different users"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by jancici on 2006-12-30
hi

I did install ubuntu 6.10 on my hp laptop nc 6220. somehow I did choose oem instalation so my first user is "oem". so first thing after login in was creating new user called "pokus". I did insert that user to same groups as oem user.

suspend to ram is working well under OEM user

but when I login as "pokus" then resuming is crashing.

I did find this in Xorg log


Error in I830WaitLpRing(), now is -734939085, start is -734941086
pgetbl_ctl: 0x3ffc0001 pgetbl_err: 0x0
ipeir: 0 iphdr: 0
LP ring tail: f8 head: 0 len: 1f001 start 0
eir: 0 esr: 1 emr: ffff
instdone: ffc1 instpm: 0
memmode: 108 instps: 2014c0
hwstam: fffe ier: 2 imr: 8 iir: 20
space: 130816 wanted 131064
(II) I810(0): [drm] removed 1 reserved context for kernel
(II) I810(0): [drm] unmapping 8192 bytes of SAREA 0xf9203000 at 0xb7b2e000

Fatal server error:
lockup


I do not uderstand what is wrong,  thanks for any tip

---

