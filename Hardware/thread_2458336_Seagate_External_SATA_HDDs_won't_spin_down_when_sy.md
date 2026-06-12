---
title: "Seagate External SATA HDDs won't spin down when system suspends."
date: 2021-02-22
forum: Hardware
---

### Post by xaxazak on 2021-02-22
When I sleep, my Seagate external 3/4/5GB SATA drives (model SRD0NF2 and similar ones) often (but not always) keep spinning until resume (which can be days). My issues are noise and wear.
I'm on Xubuntu 20.10, Kernel 5.10.0 (although 20.04 with default kernel had same problem).

HDParm doesn't work.

Is there a way I can force these to spin down during suspend?

Relevant Specs:
Asus PRIME X570-P.
UEFI.
Ryzen 5 3600.

---

### Post by TheFu on 2021-02-22
I go out of my way to force my drives to keep spinning. hdparm DOES handle that need for non-seagate external drives.  I think the start and stop of the platters is worse than leaving them spinning 24.7.365 for years.

Maybe if you post all the hdparm commands you've tried, someone could see a problem?

---

