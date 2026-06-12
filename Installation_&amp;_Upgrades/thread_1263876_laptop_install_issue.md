---
title: "laptop install issue"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by nsdemon on 2009-09-11
on ubuntu versions 8.04 and 9.04 I am getting
MP Bios Bug Timer could not connect to io-apic
and it hangs/frezzes up on boot
i know i have installed and run ubuntu on this laptop before..
what is up with this error??

I have a sony vaio PCG-GRT200 series


           ***[FONT=Arial]M[/FONT]******[FONT=Arial]od[/FONT]******[FONT=Arial]e[/FONT]******[FONT=Arial]l[/FONT]***
         ***[FONT=Arial]PCG-GRT200 S[/FONT]******[FONT=Arial]e[/FONT]******[FONT=Arial]r[/FONT]******[FONT=Arial]i[/FONT]******[FONT=Arial]es[/FONT]***
             ***[FONT=Arial]P[/FONT]******[FONT=Arial]r[/FONT]******[FONT=Arial]o[/FONT]******[FONT=Arial]cessor [/FONT]******[FONT=Arial]o[/FONT]******[FONT=Arial]p[/FONT]******[FONT=Arial]t[/FONT]******[FONT=Arial]i[/FONT]******[FONT=Arial]o[/FONT]******[FONT=Arial]n[/FONT]******[FONT=Arial]s[/FONT]******[FONT=Arial]*[/FONT]***
         **[FONT=&quot]A[/FONT]****[FONT=&quot]v[/FONT]****[FONT=&quot]a[/FONT]****[FONT=&quot]i[/FONT]****[FONT=&quot]lable[/FONT]**[FONT=&quot]: Intel®   Pentium® 4 processor 2.40B, 2.66, 2.80 GHz[/FONT][FONT=&quot]†[/FONT][FONT=&quot], Mobile Intel Pentium 4   processor[/FONT][FONT=&quot]‡ [/FONT][FONT=&quot]2.2[/FONT][FONT=&quot]0[/FONT][FONT=&quot], 2.40, 2.60 GHz-M[/FONT][FONT=&quot]**[/FONT][FONT=&quot], or Mobile Intel Celeron® processor 2 GHz[/FONT]
             ***[FONT=Arial]L[/FONT]******[FONT=Arial]2 Cache [/FONT]******[FONT=Arial]M[/FONT]******[FONT=Arial]e[/FONT]******[FONT=Arial]mo[/FONT]******[FONT=Arial]r[/FONT]******[FONT=Arial]y[/FONT]***
         [FONT=&quot]5[/FONT][FONT=&quot]1[/FONT][FONT=&quot]2 KB (CPU Integrated)[/FONT]
             ***[FONT=Arial]H[/FONT]******[FONT=Arial]ar[/FONT]******[FONT=Arial]d Disk   Drive [/FONT]******[FONT=Arial]op[/FONT]******[FONT=Arial]tio[/FONT]******[FONT=Arial]n[/FONT]******[FONT=Arial]s[/FONT]******[FONT=Arial]*[/FONT]***
         **[FONT=&quot]A[/FONT]****[FONT=&quot]v[/FONT]****[FONT=&quot]a[/FONT]****[FONT=&quot]i[/FONT]****[FONT=&quot]lable[/FONT]**[FONT=&quot]: 30, 40, 60   or 80 GB[/FONT][FONT=&quot]††[/FONT]
             ***[FONT=Arial]C/D [/FONT]******[FONT=Arial]Pa[/FONT]******[FONT=Arial]r[/FONT]******[FONT=Arial]t[/FONT]******[FONT=Arial]itio[/FONT]******[FONT=Arial]n[/FONT]***
         [FONT=&quot]C[/FONT][FONT=&quot]= 15 GB (NTFS), D= remainder (NTFS) (approximation)[/FONT]
             ***[FONT=Arial]Standard RAM [/FONT]******[FONT=Arial]o[/FONT]******[FONT=Arial]p[/FONT]******[FONT=Arial]t[/FONT]******[FONT=Arial]i[/FONT]******[FONT=Arial]ons[/FONT]******[FONT=Arial]*[/FONT]***
         **[FONT=&quot]A[/FONT]****[FONT=&quot]v[/FONT]****[FONT=&quot]a[/FONT]****[FONT=&quot]i[/FONT]****[FONT=&quot]lable[/FONT]**[FONT=&quot]: 256 MB, 512 MB, 1 GB DDR SDRAM[/FONT][FONT=&quot]‡‡ [/FONT][FONT=&quot](Ma[/FONT][FONT=&quot]x[/FONT][FONT=&quot]. 1 GB) (Unbuffered DDR266 SO-DIMM gold lead contacts)[/FONT]

---

### Post by nsdemon on 2009-09-11
anyone know what i can do to fix my error?

---

### Post by ronparent on 2009-09-11
I had two desktops and a laptop, none of which would run 9.04 without freezing. I used F6 at the first screen following language selection on the live cd boot to x out apic and lapic for the boot. When That fixed the problem I proceeded with the install from the live cd. You can try it with the live cd before commiting to the install. If installed from the live cd the kernel options noapic,nolapic will be automatically added to the boot options.

---

