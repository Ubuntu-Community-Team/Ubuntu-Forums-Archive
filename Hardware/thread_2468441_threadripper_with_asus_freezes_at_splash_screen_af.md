---
title: "threadripper with asus freezes at splash screen after latest BIOS upgrade"
date: 2021-10-29
forum: Hardware
---

### Post by capt_mckenzie on 2021-10-29
I have tried the standard workrounds which have worked in the past by editing grub
At Linux boot line I remove quiet splash and have tried booting with mce=off
nosplash
nomodeset
and all three
but NBG

Anything else I can try?
capt

---

### Post by capt_mckenzie on 2021-10-29
additional info

ubuntu 20.04
asus mb rogzenith extreme
threadripper 2990
and tried replacing quiet splash with dis_ucode_ldr
capt

---

### Post by capt_mckenzie on 2021-10-31
Solved

None of the editing grub or trying to restart via recovery options worked so I cleared CMOS and loaded UEFI  default standard BIOS option dumping the various overclocking etc.  
After reset booting was OK.  I will leave system at its default state for a day before trying to up the memory speed etc.
capt

---

