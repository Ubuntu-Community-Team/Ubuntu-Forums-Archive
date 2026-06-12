---
title: "module doesn't show in /proc/ioports"
date: 2008-07-20
forum: General Help
---

### Post by mikea87 on 2008-07-20
I have a simple parallel port driver to flash color LEDs. There is any other driver that takes this port under 0x378 (I switched it off). I insmod my driver and it loads easily but when I check /proc/ioports there is nothing under 0x378 adress. Why? Thanks in advance

There was some functions missing (with suitable arguments): 

```
check_region(); 
request_region();
inb();
outb();

```

---

