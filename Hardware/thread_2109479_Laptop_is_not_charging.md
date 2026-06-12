---
title: "Laptop is not charging"
date: 2013-01-27
forum: Hardware
---

### Post by rawa93 on 2013-01-27
I have a Sony Vaio VPCSB1X9E ([Specification]("http://www.sony.co.uk/product/vaio-s-series/vpcsb1x9e")) and on every Linux distro I get the same charging issue. I think it is related to the Linux Kernel but I'm not sure. I'm running Ubuntu 12.10. Basically when I plug in the charger the green light on the power button goes on and off rapidly instead of staying as it is.  I don't have this issue on Windows 7 or 8. It doesn't charge the battery and I get annoying warnings stating that it is charging for a second and then that it is on low battery. Unfortunately I can't find any useful help on google regarding this issue. I have tried so many things but none worked. Even if I remove the battery and run the laptop only with the charger connected, the laptop switches off after some random time. This indicates that it is not a battery issue but an issue regarding how the laptop receives energy I guess. I would appreciate any help I could get as I really love ubuntu and want to stick to it. Thank you.

---

### Post by tgalati4 on 2013-01-27
The specs show a "stamina" mode and a "speed" mode.  This is probably a BIOS-managed power draw that the Linux kernel doesn't know how to handle.  I would first search for a BIOS upgrade and reflash that.  If no change, then I would file a bug against the kernel--since you haven't found any workarounds on the web.  Sonys are known for the proprietary chips and protocols--not linux-friendly usually.  Thinkpads are ugly, slow, but quite compatible.  Sony's are sleek, colorful, and good for running Windows8.

---

### Post by offgridguy on 2013-01-27
> **tgalati4 said:**
>   thinkpads are ugly, slow, but quite compatible. 
+1;)

---

### Post by rawa93 on 2013-02-01
> **tgalati4 said:**
> The specs show a "stamina" mode and a "speed" mode.  This is probably a BIOS-managed power draw that the Linux kernel doesn't know how to handle.  I would first search for a BIOS upgrade and reflash that.  If no change, then I would file a bug against the kernel--since you haven't found any workarounds on the web.  Sonys are known for the proprietary chips and protocols--not linux-friendly usually.  Thinkpads are ugly, slow, but quite compatible.  Sony's are sleek, colorful, and good for running Windows8.

Thanks for your help. The bios update didn't help. How can I report this bug?

---

### Post by offgridguy on 2013-02-01
> **rawa93 said:**
> Thanks for your help. The bios update didn't help. How can I report this bug?
If your laptop is incompatible with linux, you can help everyone by posting here.

[http://ubuntuforums.org/showthread.php?t=1543009](http://ubuntuforums.org/showthread.php?t=1543009)

---

