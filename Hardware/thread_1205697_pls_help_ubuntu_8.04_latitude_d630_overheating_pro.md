---
title: "pls help ubuntu 8.04 latitude d630 overheating problems?"
date: 2009-07-06
forum: Hardware
---

### Post by misha680 on 2009-07-06
I seem to have problems with ubuntu 8.04 on my latitude d630 overheating.

This happens with _no_ nvidia driver. It freezes/crashes and requires hot restart. Actually seems _better_ with nvidia driver 185.18.14. I thought it was better with acpi=off but not sure.

My only hints are:
```

[ 4426.121328] NVRM: Xid (0001:00): 6, PE0001 

```

with Nvidia driver installed and:
```

[   81.761541] gnome-power-man[7259]: segfault at 0 rip 41141a rsp 7fff9b6539c0 error 4

```

from gnome power manager. Thank you

Misha

---

### Post by mhgsys on 2009-07-06
open a terminal and type:
```


sudo apt-get install computertemp

```
after that right click a panel, click add to panel and select computer temperature monitor.

That way you can monitor the temperature set an alarm etc.



*If it's not there, reboot, It will be there after 
**(Don't know if maybe it also appears by restarting gdm)

If you don't get any output on the computertemp-sensor, install libsensors4 & lm-sensors as well.
after that run 
```

sudo sensors-detect

```

I suggest you clean out the fan, and monitor your temperature

---

### Post by misha680 on 2009-07-09
Thanks am trying this out. Not happy about overheating issues.

---

