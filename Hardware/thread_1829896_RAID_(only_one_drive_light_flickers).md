---
title: "RAID (only one drive light flickers)"
date: 2011-08-20
forum: Hardware
---

### Post by RayChangTW on 2011-08-20
I just noticed that only one HD light is flickering with disk I/O.

-Nvidia BIOS says "healthy" when starting the computer.

-Also, I tried this:

me@me-M68M-S2P:~$ sudo dmraid -r
[sudo] password for me:
/dev/sdb: nvidia, "nvidia_bbeggidc", mirror, ok, 1953525166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_bbeggidc", mirror, ok, 1953525166 sectors, data@ 0
me@me-M68M-S2P:~$

Does anyone have any ideas what might be wrong?  Are there any other tricks I might try with dmraid?

Thank you.

---

