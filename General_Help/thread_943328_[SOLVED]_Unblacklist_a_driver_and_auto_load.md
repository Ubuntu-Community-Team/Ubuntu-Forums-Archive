---
title: "[SOLVED] Unblacklist a driver and auto load"
date: 2008-10-10
forum: General Help
---

### Post by MegaJim on 2008-10-10
Ok, so I previously needed to blacklist the rt73usb driver which i did by editing /etc/modprobe.d/blacklist to contain the line 'blacklist rt73usb'

However now I need to use this driver again I have removed the blacklist entry, but every time I restart I need to insert the module into the kernel again manually using sudo modprobe rt73usb.

My question is, why is this happening, and what can I do to get the driver to load automatically?

Thanks very much

---

### Post by llebegue on 2008-10-10
Have you tried 

```

sudo insmod rt73usb

```

---

### Post by MegaJim on 2008-10-10
Thanks, but insmod isn't even able to load the module; it shows up as an option for tab completion but when the command is run it cannot find the module.

Looking at its manpages the proper program to use is modprobe, and it doesn't describe anything about auto-insert, it in fact seems rather slim and pale in comparison.

---

### Post by MegaJim on 2008-10-10
I found that I can get the module to load at boot time by adding rt73usb to /etc/modules !

---

