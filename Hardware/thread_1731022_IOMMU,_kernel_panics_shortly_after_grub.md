---
title: "IOMMU, kernel panics shortly after grub"
date: 2011-04-16
forum: Hardware
---

### Post by TechZilla on 2011-04-16
Linux Zilla64 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux,

attached gziped hwinfo/dmidecode/lspci

Supermicro H8SGL-F-O
RAM is registered
BIOS 1.1c

I have a strange, (possible bug, either HW or kernel). When IOMMU is enabled, via bios, kernel panics shortly after grub.  I'm not sure how to get a log (or even if logging at that point is possible).

Problem only happens when IOMMU is enable AND if both of my PCI-e cards are plugged in
ATI Radeon HD 5670
ASUS Zonar DX 

if only one is plugged in, either the ASUS or ATI, the kernel boot correctly. But when both are in with IOMMU enabled, then... BAM PANIC!!!

Getting the info, might be possible only with my digital camera, but i wrote parts of a few lines down.

```

{HEX&Chars}Page Fault{HEX&Chars}
{HEX&Chars}Bad Area{HEX&Chars}
{HEX&Chars}No Sephamore{HEX&Chars}
{HEX&Chars}Opps End{HEX&Chars}
{HEX&Chars}Exit_Notify{HEX&Chars}

```

this is just some examples, i could go the camera route, if necessary...don't really want to risk having to go through another fsck

Any ideas, i'm at the newest BIOS, not sure who's issue this is. I can file a bug report with the necessary group once I figure out who that is.


appreciate the help, just though this should be told
I'm otherwise running great, just wish I could use IOMMU

---

### Post by TechZilla on 2011-04-19
I submitted a bug, just no idea what else to do.  Figured it was my duty to let the devs at least know about the issue.

---

