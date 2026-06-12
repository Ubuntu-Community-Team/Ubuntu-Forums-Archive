---
title: "Checking for bad memory"
date: 2020-09-28
forum: Hardware
---

### Post by plizzba on 2020-09-28
I suspected I had some bad memory but I had an awful time verifying this. I am describing the solution I found for checking memory so that others might avoid the experience.

In the past I used MemTest86 from the grub menu. But apparently this is not present (and can't be made functional) on UEFI systems. So, I went and installed the free version of MemTest86 (8.4 for UEFI systems). I was able to boot MemTest86, but the screen stays black so I couldn't see what was going on.

Eventually, I found that I could install stress-ng (via `apt install stress-ng`). To check my memory, I would first run `free -h` to find out how much memory I currently had free (listed under `available`). If this says 6Gi then I'd run something like
```
stress-ng --vm 4 --vm-bytes 6G --vm-method all --verify --timeout 15m
```
to run 4 processes testing 6 gigabytes of memory for 15 minutes. This seemed to pretty quickly find my bad memory (though I'm sure there are better settings for `stress-ng`).

I did the usual think of going down to one stick, checking it, then adding new dimms one at a time and checking each one. I found the bad memory pretty quickly. (In my case the 15 minutes was overkill for detecting the bad ram, though I plan to test the remaining RAM with something much bigger than 15 minutes when I get a chance.)

Remarks:
1. I'm sad that MemTest86 is now missing from GRUB on UEFI systems. It would be great if it could be returned or replaced with something similar.
2. I regret making the unintensional mistake of buying a computer whose motherboard doesn't support ECC.

---

### Post by TheFu on 2020-09-28
Did you consider tweaking the timing settings for the RAM?  As RAM gets faster, we are seeing much more that doesn't quite meet the vendor's specs. Backing off a little on the refresh speed and slightly increasing the voltage can do wonders.

---

