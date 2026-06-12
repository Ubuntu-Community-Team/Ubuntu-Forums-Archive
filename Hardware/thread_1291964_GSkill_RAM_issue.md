---
title: "GSkill RAM issue"
date: 2009-10-15
forum: Hardware
---

### Post by Norami on 2009-10-15
I've all of the sudden been having problems with my RAM in Ubuntu. I'm using two GSkill 2GB sticks. In post it reads the memory at 4GB, but when I look through my system information in Ubuntu, it's only reading it as 2.5GB. Is there some sort of configuration I'm missing? or a patch of some sort for this issue? I've contacted Gigabyte (which is my motherboard) about this, and they said since it's coming up in post as 4GB, there's nothing they can do to help me. Any help or insight would be appreciated.

---

### Post by Giblet5 on 2009-10-15
Are you running 32-bit Ubuntu, or 64 bit Ubuntu.

For 32-bit, that's normal.

(Do the math: 2**32 - really 2**31 < 4G)

If your BIOS settings allow it, you can turn off the (Remap Memory) option and you'll get around 3G.

I'd switch to 64-bit...

---

### Post by Norami on 2009-10-16
I'm using 32-bit. I don't quite understand the math part. And I'm not sure why this would effect the memory. Any other 32-bit OS I've used, it always reads it as 4GB, sometimes 3.8GB. Ubuntu Studio read it as 4GB even. Same as Windows, Fedora and Mac OS X.

I would switch to 64-bit if more software was supported, but right now it's easier for me to use 32-bit.

---

