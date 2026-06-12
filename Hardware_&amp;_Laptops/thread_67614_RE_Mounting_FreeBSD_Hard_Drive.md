---
title: "RE: Mounting FreeBSD Hard Drive"
date: 2005-09-20
forum: Hardware &amp; Laptops
---

### Post by socialvictim on 2005-09-20
Hello Everyone!

I am trying to mount a FreeBSD hard-drive of mine into /mnt/second_hdd

Any clue as to how I can do this?

I have tried everything and asked many people.  The best advice they gave was that I should enable UFS support in the Ubuntu Kernel.  Is UFS support already enabled in the Kernel, or not?

Someone PLEASE let me know if you have the answer!

Socialvictim

---

### Post by kq6up on 2006-08-28
#mount -t ufs -o ufstype=5xbsd /dev/hdc11 /media/hdc11/

---

### Post by GoBieN on 2006-09-07
@kq6up

Thank you, worked like a charm, except use mount -r -t ufs -o ....

Because kernel has only read-only ufs support compiled, dmesg told me so anyways.

---

