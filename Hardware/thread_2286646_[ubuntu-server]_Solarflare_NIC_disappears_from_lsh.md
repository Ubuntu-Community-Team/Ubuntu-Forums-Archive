---
title: "[ubuntu-server] Solarflare NIC disappears from lshw, dmesg, system"
date: 2015-07-13
forum: Hardware
---

### Post by computercolin2 on 2015-07-13
Hello I have a strange issue. After reboot, Solarflare SFN5162F NIC (a PCI-Ex SFP device) has disappeared. After rebooting several more times, it has not come back.

Previously Solarflare showed up in dmesg and lshw.

Additionally, something strange is going on with insmod.
```

$ sudo insmod sfc
insmod: ERROR: could not load module sfc: No such file or directory

```

So it doesn't like that, however, if I find the module manually:
```

$ cd /lib/modules/3.16.0-43-generic/kernel/drivers/net/ethernet/
$ sudo insmod sfc
insmod: ERROR: could not insert module sfc: No such device

```

It complains no appropriate hardware is installed.

System is Ubuntu Server 14.04.02
Kernel 3.16.0-43-generic
```

$ uname -a
Linux LinuxMachine 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

*linux-image-extras* are installed

---

### Post by computercolin2 on 2015-07-13
Basically it seems this is either a device issue (faulty NIC) or bug with kernel module/firmware. What commands can I use to debug? *lshw* shows nothing, is there another command that would show a "missing" device on PCI-E, even if kernel modules were not working?

---

