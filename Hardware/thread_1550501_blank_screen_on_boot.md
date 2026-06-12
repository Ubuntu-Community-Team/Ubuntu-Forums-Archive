---
title: "blank screen on boot"
date: 2010-08-11
forum: Hardware
---

### Post by barna on 2010-08-11
Hi,
I have a Dell Inspiron 1564, for which everything worked out of the box. 
BUT... at every now and then, about once from 6 boots, I get a blank screen after the boot, it does not react to any keyboard events, only to Ctrl+Alt+Del (reboot) or the Power Button (halt). 
I can not even get a console (Ctrl+Alt+F1, etc).
Any idea? What should I check? 

Thanks

---

### Post by barna on 2010-08-27
The boot splash screen was responsible for this problem, it seems. 
To disable the boot splash screen, edit (as su) /etc/default/grub, and remove splash from this line:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
and then run (as su) update-grub. I also removed the quied option, to have more diagnostics. 
After this, I have no more frozen screens on startup.

---

