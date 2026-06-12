---
title: "Bad graphics performance with Intel Series 4 graphics controller"
date: 2009-11-09
forum: Hardware
---

### Post by sgerke on 2009-11-09
Hi all,

I have major problems with the graphics performance (especially when using an 1920x1080 external display, it is much better using the laptop's screen with 1280x800 resolution) of my Dell Latitude E4300 with 4GB RAM and its Intel Series 4 graphics chipset under Kubuntu Karmic (and before under Ubuntu Jaunty). E.g. when switching applications with Alt+Tab, I can see drawing parts of the GUI before other parts of the activated window and when pressing Alt+F1, it takes about half a second for the KMenu to appear.  According to the dmesg output (see attached), it seems to be a problem with MTRR write-combining range for video memory (0x0e0000000) not set up correctly.
dmesg:
```
[    3.425976] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[    3.425979] [drm] MTRR allocation failed.  Graphics performance may suffer.
```


/proc/mtrr:
```
reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg02: base=0x0ddc00000 ( 3548MB), size=    4MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable
reg04: base=0x11c000000 ( 4544MB), size=   64MB, count=1: uncachable
```
I tried the enable_mtrr_cleanup kernel parameter, but it did not work:
```
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size

```
I assume it did not work because on my system, there are only 7 mtrr entries available, causing the kernel mtrr cleanup code not being able to set up the registers for 32 GB (according to the mtrr provided from the BIOS) correctly.
Then I played around with mtrr_gran_size / mtrr_chunk_size (I set both of them to 64M), resulting in following MTRR:
```
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-back
reg03: base=0x0d0000000 ( 3328MB), size=  128MB, count=1: write-back
reg04: base=0x0d8000000 ( 3456MB), size=   64MB, count=1: write-back
reg05: base=0x100000000 ( 4096MB), size=  256MB, count=1: write-back
reg06: base=0x110000000 ( 4352MB), size=  128MB, count=1: write-back
```

As there are already 7 regions in use, the X-server is not able to add another write-combining range for the memory assigned to the graphics controller. I tried to remove the smallest region (4) from the MTRR table and adding the write-combining range manually with the following script:
```
echo "disable=4" >| /proc/mtrr
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
```
resulting in the following MTRR:
```
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-back
reg03: base=0x0d0000000 ( 3328MB), size=  128MB, count=1: write-back
reg04: base=0x0e0000000 ( 3584MB), size=  256MB, count=1: write-combining
reg05: base=0x100000000 ( 4096MB), size=  256MB, count=1: write-back
reg06: base=0x110000000 ( 4352MB), size=  128MB, count=1: write-back
```
which seems to be OK, but performance did not actually improve, I even had the impression that the performance was worse than before.

I also tried the mtrr-uncover utility and the fix_mtrr.sh script I found while googling for possible solutions.

Right now, I don't know what I could try next. I updated the BIOS to the latest version, but the MTRR did not change.

Has anyone an idea how to proceed or what to try next? 


Thanks in advance for your help,
Sebastian

---

### Post by sgerke on 2009-11-10
Anyone an idea? It might beven help to tell me where to file a bug report.

Best,
Sebastian

---

### Post by sgerke on 2009-11-13
bump

---

