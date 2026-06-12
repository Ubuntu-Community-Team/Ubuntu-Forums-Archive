---
title: "Sony Vaio TZ92 Problem with speed governor"
date: 2009-05-29
forum: Hardware
---

### Post by Numer0bis on 2009-05-29
Hello everybody

I have a slight problem with the speed governor. After boot-up whenever it is on AC or running on batteries the speed governor is always on performance and the cpu is running at 1.3 ghz (max.). I installed sysfsutils and tried to change the behaviour by writing in 

```

devices/system/cpu/cpu0/cpufreq/scaling_governor = ondemand

```

in /etc/sysfs.conf.

But still it will stay on performance mode. Has anyone a solution to this issue or any idea why it stays on performance all the time.
 
Thanks for any help in advance.

Greetz

Numer0bis

---

