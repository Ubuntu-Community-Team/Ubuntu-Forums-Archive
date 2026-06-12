---
title: "Big big"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by milou on 2008-01-12
I have a big big problem with a fresh install of gutsy on a D900t laptop.
I had before edgy updated to gutsy and it worked ok, but I wanted to make a fresh install.

I tried first with a Gutsy DVD, but during the files copy, the power supply just shutted off !
I tried with a install CD, it worked.
But after the reboot and use of Gutsy, the power supply just shuts off RANDOMLY !!! I have no idea why, no info in the logs, nothing !

I succeeded in doing a apt-get update/upgrade after several halts/reboots, but this did not change anything. I thought that maybe this was a kernel/module problem but this is not.

I tried to reboot and immediatly made (ok, all with sudo) :
/etc/init.d/networking stop
/etc/init.d/gdm stop
/etc/init.d/hdparm stop
/etc/init.d/ stop

and modprobe -r thermal fan processor

but still randomly (before 15-20 min) the power supply brutally halts !

I have a dual-boot with a minimal windows install. And it seems to work however with windows ... no power supply brutal halt after 1h in windows ... This means that this is probably not a laptop dysfunction.

Where must I search for a solution ? Please help, ....
__________________

---

### Post by bapoumba on 2008-01-12
Moved to "Hardware & Laptops" and deleted duplicate.

Overheating ?
You can check with:
```
acpi -V
```

---

