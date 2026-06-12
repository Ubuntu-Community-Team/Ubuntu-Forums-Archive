---
title: "Wrong Graphics Card Displayed"
date: 2011-01-09
forum: Hardware
---

### Post by afbase on 2011-01-09
Hello,

I installed the latest NVIDIA driver, x86_64-260.19.29, on my computer today (from the nvidia website).  It displays ```
04:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)
``` in my lspci command instead of _Geforce GTX 260M_.

I run lucid lynx 10.04

How do i correct this?

---

### Post by dandnsmith on 2011-01-09
I believe the *lspci* command displays a string obtained by interrogating the hardware directly.

HTH

---

### Post by afbase on 2011-01-09
> **dandnsmith said:**
> I believe the *lspci* command displays a string obtained by interrogating the hardware directly.

HTH

I know its a 260M because the other day I was able to run CUDA programs perfectly fine.    Now I am not able to.

---

### Post by afbase on 2011-01-09
I  looked through my Xorg log and I found it displays a 9400:
```

(--) PCI: (0:0:3:5) 10de:0aa3:10de:cb79 nVidia Corporation MCP79
Co-processor rev 177, Mem @ 0xf0600000/524288
(--) PCI:*(0:4:0:0) 10de:0862:1028:02a1 nVidia Corporation C79
[GeForce 9400M G] rev 177, Mem @ 0xcc000000/16777216,
0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x00004000/128

```
I booted into windows to see if I got the same results.  Sadly, it too says 9400 (see the picture)

---

### Post by afbase on 2011-01-09
I simply called dell support.  It was a bios setting to get the right graphics card displayed.

---

### Post by dandnsmith on 2011-01-09
Now you've puzzled me.
What were the settings before and after, to have this effect?

---

### Post by Firezap on 2011-01-09
Maybe his motherboard had an integrated Nvidia card. And he forgot to select the new card in the Bios settings. Just a thought.

---

### Post by afbase on 2011-01-09
> **Firezap said:**
> Maybe his motherboard had an integrated Nvidia card. And he forgot to select the new card in the Bios settings. Just a thought.

thats about halfway correct.  I disabled integreated and hybrid graphics to get the correct graphics card to display.

---

