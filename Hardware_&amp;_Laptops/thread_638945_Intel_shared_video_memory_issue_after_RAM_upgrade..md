---
title: "Intel shared video memory issue after RAM upgrade.  No X."
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by mthompson1981 on 2007-12-12
I just put two 2GB sticks of RAM in my Acer Aspire 9410 laptop running Gutsy.  The BIOS only sees 3GB of RAM, however everything works fine in Vista and memtest86+ checks out ok.

The machine works fine until Xorg starts, when the display shows a bunch of random junk.  I can Ctrl+Alt+F1 to another console and login, the system is working fine otherwise.

If I remove the second 2GB stick of RAM, everything works fine as well.  I tried using the VESA xorg drivers with the same result.

The chipset is intel 945GM

Here is some info when running with 2GB (Xorg WORKING):

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f690000 (usable)
[    0.000000]  BIOS-e820: 000000007f690000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.

and the MTRRs:

reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x7f700000 (2039MB), size=   1MB: uncachable, count=1
reg02: base=0x7f800000 (2040MB), size=   8MB: uncachable, count=1
reg03: base=0xb0000000 (2816MB), size= 256MB: write-combining, count=1



With 3GB:

I get these messages:
PCI: Cannot allocate resource region 2 of device 0000:00:02.0
PCI: Failed to allocate mem resource #2:10000000@0 for 0000:00:02.0

PCI device 02.0 is the video card.  with a mem=2G param, those messages go away, but the video still doesn't work in Xorg.

[    0.000000] Linux version 2.6.23.9-matt (root@matt-laptop) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Mon Dec 10 23:43:41 EST 2007
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf690000 (usable)
[    0.000000]  BIOS-e820: 00000000bf690000 - 00000000bf700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf700000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 2166MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.


And the MTRRs:
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xbf700000 (3063MB), size=   1MB: uncachable, count=1
reg03: base=0xbf800000 (3064MB), size=   8MB: uncachable, count=1


I tried fixing up the MTRRs in single user mode before starting X, so that the video memory was set write-combining.  Xorg was unable to set this because the 256M video ram is at 0xb0000000 which overlaps with the reg01 write-back mtrr.

Also tried mem=2G, however the MTRRs stayed the same.  Seems the kernel is setting the write-back ranges for all detected RAM reported by the BIOS, and not by the mem= parameter.

Does anyone have any ideas?  I  would at least like to have both sticks installed to take advantage of dual channel, even I can only have 2GB available to Ubuntu.  Unfortunately I can't return or exchange the RAM.

Cheers

---

