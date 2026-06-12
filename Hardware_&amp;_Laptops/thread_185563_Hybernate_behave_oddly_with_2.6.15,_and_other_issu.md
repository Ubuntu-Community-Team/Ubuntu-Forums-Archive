---
title: "Hybernate behave oddly with 2.6.15, and other issues"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by perce on 2006-05-31
I have updated from Breezy to Dapper, and with the new kernel shipped with it
I can hybernate only once, the second time, if I try, the screen is locked too. If I try to hybernate manually by echo disk > /sys/power/state the kernel freezes.

I think this is more a kernel issue than an Ubuntu issue, because hybernate still works with the old 2.6.12. However, using the old kernel is inconvenient because,
when I use the 2.6.12, the system bell doesn't ring anymore (it worked on Breezy) and all mixer channel are muted at each reboot.

I would file a bug report, however I bought a laptop without brand name five years ago and I can't be more specific than I am here. It's a pity that my system worked much better before the upgrade :(

---

### Post by perce on 2006-06-01
It sounds wierd to replay to myself...

I made some investigation and I discovered the source of my problems with hybernate: the kernel 2.6.15 uses apm instead of acpi. I've tried to remove the apm module and insert some acpi module manually, but all what I got was a "not such device" error.   

How can I swich from apm to acpi? apm is very unstable on my computer, so no acpi implies no more Ubuntu and back to Debian, but I'd really like to stay here.

---

### Post by perce on 2006-06-01
This thread has turned into a blog :oops: 

The problem with the kernel 2.6.15 has been solved: they put a threashold year,
so that ACPI is not activated if the BIOS is older than 2000. This setting can be overridden by adding the option acpi=force to the kernel line in /boot/grub/menu.lst.

---

