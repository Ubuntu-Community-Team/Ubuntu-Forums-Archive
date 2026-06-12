---
title: "Recommendations for RAM exapansion?"
date: 2008-04-30
forum: Hardware
---

### Post by amityak on 2008-04-30
working on my GF's computer i couldnt notice its running slower then a turtle after smoking to much marijuana i decided to give it a closer look.

lshw showes that:

  ```
   *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up

```

which is for itself could be okay unless the fact of the very strange memory size:

```
     *-memory
          description: System memory
          physical id: 0
          size: 383MB
```

since this size of 383MB wasnt familiar to me (and to all opinions is quite small) i decided to open it. I was schocked, 3 SDRAM sticks ... 3 and still so slow?

well apperantly one is at the size of 62MB, 256Mb and something non undestandable else.

Now to my question: should it theoretically not be better to throw the weird SIM away, i beleive it might slow all down?

Shouldnt it be better to throw all 3 away and to get a decent memory? I wouldnt wanna go to far though, remembering its just a modest 800MHZ P3.

I would be happy for opinons and recommendations,

Cheers, Amit.

---

### Post by Sef on 2008-04-30
I would get 512 mb for it.  I believe you can put up to 2 gb ram, but for that machine, 512 mb ram should do just fine.

Use a live cd and do a mem86 test to make sure the ram is still good.

---

