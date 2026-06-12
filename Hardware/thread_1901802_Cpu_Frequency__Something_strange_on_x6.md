---
title: "Cpu Frequency : Something strange on x6"
date: 2011-12-29
forum: Hardware
---

### Post by dracula001 on 2011-12-29
Hello all, i noticed something that i could not understand at all. With  2.6.32 kernel the Cpu frequency monitor show :
170 ghz
2,50ghz
3.30 ghz
3.70 ghz

With kernel 2.6.38  it show

800 mhz
1,70 ghz
2,50 ghz
3,30 ghz

My cpu is the Athlon x6 1090t black edition.   I noticed also that with kernel 2.6.32 that 3,70 ghz option is not  possibile to select it it's just over there but can not use it.

Why this happen? Is because kernel 2.6.32 does not fully support this cpu?

Thank you

---

### Post by 2F4U on 2011-12-29
If I remember correctly, AMD, who provides the kernel support for their CPU's, introduced a bug, which was only fixed in later kernel versions.

---

