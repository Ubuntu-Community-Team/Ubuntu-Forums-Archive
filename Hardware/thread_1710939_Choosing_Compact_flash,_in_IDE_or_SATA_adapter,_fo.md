---
title: "Choosing Compact flash, in IDE or SATA adapter, for bootable Ubuntu install?"
date: 2011-03-20
forum: Hardware
---

### Post by wb0gaz on 2011-03-20
Seeking "it works" hardware advice:

Looking for recommendation for 4-8GB compact flash card I can use in a compact flash/IDE or compact flash/SATA adapter for purpose of installing Ubuntu 10.04.02 server (10.10 installer doesn't get past initial "loading boot logo" on this machine so I need use 10.04.02).

My initial experiments using a Compact Flash/IDE adapter failed (the Sandisk Ultra II I believe due to lack of any DMA capability; the Transcend TS4GCF133 has UDMA4 but still the boot sequence failed again I think due to DMA issues.)

My initial experiments using a Compact Flash/SATA adapter failed (the Sandisk Ultra II would boot but could not run properly, reporting Bash library relocation errors; the Transcend TS4GCF133 would boot but appeared to have extremely slow write-single-block access time, leaving the root filesystem still mounted during a shutdown operation, among other symptoms.)

Some quick searching suggests this (installing ubuntu onto compact flash for purpose of bootable system) is a source of trouble, so I seek advice (or direction on where to go) as the experimental approach has consumed much time and a little money too.

Thank you,

Dave

---

### Post by netslacker on 2011-07-01
Did you get anywhere on this?

I have two different adapters and two different CF cards and I can't get any combination of CF card to Adapter to work.

I can install to CF card using an ordinary USB reader, but once that card goes into either of the SATA adapters it will not boot up. One hangs during POST and the other gets mostly booted then hangs.

Any suggestions?

using 11.04.

---

### Post by wb0gaz on 2011-07-01
Nothing very useful. I think many of the higher-speed flash devices are optimized for throughput in a digital camera (writing large contiguous files in single-thread environment) and the specific Transcend type I was experimenting with seemed set up this way - several-second pauses in OS operation while CF card would do it's writing, which was not acceptable. I went back to a lower-end Sandisk CF card (4GB capacity) and got it working on one particular machine (VIA C3 based, about 6 years old, using a 2.5"/CF adapter card and it's internal IDE port) and got Ubuntu 10.04 server (to which I added LXDE) going; I don't think any special kernel options were needed. On another machine same set-up not able to boot at all (passed BIOS but Kernel hung). I was not successful with any SATA/CF adapter (tried several, hoping the adapter could mask the differences among CF cards and expose a "pure" SATA device to a motherboard SATA port), and a cheap SATA/IDE adapter, set up as a daisy-chain SATA->IDE->CF, also didn't work (don't remember the failure mode, but $6 wasted there.)

---

