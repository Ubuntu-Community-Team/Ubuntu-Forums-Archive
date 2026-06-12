---
title: "Intrepid/8.10 HPT372A/372N doesn't work anymore"
date: 2008-11-02
forum: Hardware
---

### Post by XeeleeUniversum on 2008-11-02
Hi,

I updated to Intrepid a couple of days before. Allmost everything will be ok, but my HPT372A/372N PATA controller won't be detected anymore.

I got the following upon kernel boot:
```

[    6.896076] pata_hpt37x 0000:05:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.896083] pata_hpt37x 0000:05:01.0: PCI INT A disabled

```

lspci gave me this:
```

05:01.0 RAID bus controller: HighPoint Technologies, Inc. HPT372A/372N (rev 02)

```

uname -a:
```

Linux deimos 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux

```

The controller is running smoothly while running Ubuntu with the old Hardy kernel (2.6.24-21-generic). But it couldn't be a permanent solution. :)

Yours
Alex

---

### Post by dracko007 on 2008-11-17
Hi Alex,
i have the same error :( and i want to ask if you have an answer for this problem. 

Yours
Daniel

---

### Post by soulstorm666 on 2008-11-20
same problem here

---

### Post by PLI200872 on 2008-11-23
Same here.
Note that on Hardy, it was using .../ide/pci/hpt366.ko that has disappeared in Intrepid.

I never tried .../ata/pata_hpt366.ko on Hardy must be somewhat linked ...

Anyhow, solution is urgently requested !!

---

### Post by PLI200872 on 2008-11-24
In the kernel sources, there is a pata_hpt3x2n that doesn't seems to be build with the standard ubuntu kernel. Does someone succeeded in building it and using it ?

---

### Post by giovannilenzi on 2008-11-25
Hi
I've the same problem!
I used the raid with ubi 8.04 and I tried to install intrepid in a new disk attached to the same HPT372a but the installation cd does not see any disk on the raid

---

### Post by VorDesigns on 2009-02-07
Hmm, guess I won't be going to Intrepid any time soon; I've got the opposite Problem on Hardy, an HPT372 based hardware mirror is seen as two drives.

---

