---
title: "AGP aperture problem"
date: 2009-05-07
forum: Hardware
---

### Post by kooky_LT on 2009-05-07
Hi,
I have problem with AGP aperture size

kooky@kooky-T43p:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
_reg01: base=0x03ff00000 ( 1023MB), size=    1MB, count=1: uncachable_
reg02: base=0x0c0000000 ( 3072MB), size=  128MB, count=1: write-combining

I think that underlined parameter must be more than 1MB. Any ideas?

I use IBM ThinkPad T43p with ATI mobility FireGL V3200 graphics card.

Thnx.

---

