---
title: "Is necessary use fstrim on nvme-ssd ? [Dell xps 15 9550]"
date: 2017-02-15
forum: Hardware
---

### Post by vincenzonorman on 2017-02-15
Hi guys, 
as you can see in the title i have to ask you if it is necessay to use the fstrim on a nvme ssd, specifically on a dell xps 15 (9550).
I'm asking because surfing the web i have read that isn't necessary to use fstrim on this ssd type.
Any justified opinion and/or advise will be well accepted.

Thank you.

---

### Post by oldfred on 2017-02-15
Where did you see that info? I'd be interested.

But Arch which normally has good info says this:
       NVMe trim, but not discard
[https://wiki.archlinux.org/index.php/Solid_State_Drives/NVMe](https://wiki.archlinux.org/index.php/Solid_State_Drives/NVMe)

---

### Post by vincenzonorman on 2017-02-16
Search here goo.gl/e6QY2I for this phrase "Partitioning is comparable with memory cards (so no /dev/sdb2 but for  example /dev/nvme0n1p3), TRIM is no longer required, you might have to  check if your BIOS will boot from it, tools as hdparm or smartmontools  will not work or only partially, etc." .
It made me doubt so i asked.
It's my first time with an nvme drive, so i don't want to waste it.

---

