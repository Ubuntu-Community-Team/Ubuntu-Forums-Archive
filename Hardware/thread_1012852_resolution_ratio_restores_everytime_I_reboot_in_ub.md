---
title: "resolution ratio restores everytime I reboot in ubuntu 8.10"
date: 2008-12-16
forum: Hardware
---

### Post by pingwei12 on 2008-12-16
i reinstall ubuntu8.10 recently, i activated ATI Driver in System/Administration/HardwareDriver,  after i rebooted my login window turned smaller, but it turns fine  as long as i typed password. in the X-Window, the resolution ratio is 1280*1024 that is too high for my Samsung 17" monitor (1024*768), to solve this i change the parameter in Application/Accessories/ATI Catalyst Control Center, in Display Manager i choose Desktop area  'preferred' or '1024*768' refresh ratio 'preferred' or '85Hz' then Apply. now it is solved.
But if I rebooted or logout, everything restored! It bothered me a lot!
Can you help me, my friends! Thank you!

---

### Post by linux_tech on 2008-12-16
In a terminal try
```
xrandr -s 1024x768 
``` or whatever resolution

---

