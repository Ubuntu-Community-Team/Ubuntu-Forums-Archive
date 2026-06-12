---
title: "need help with Virtual box"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by malfist on 2008-01-17
When installing VirtualBox, it threw an error while trying to start and said to check dmesg, this is what dmesg said:
```

 vboxdrv: Trying to deactivate the NMI watchdog permanently...
[266579.994603] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[266579.994605] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.

```

I assume there is a config file somewhere I need to edit but I have no idea which one, and why VirtualBox needs to change that. Can someone help me out?

edit: added nmi_watchdog = 0 too kernel params in /boot/grub/menu.1st on ubuntu's main boot.

---

