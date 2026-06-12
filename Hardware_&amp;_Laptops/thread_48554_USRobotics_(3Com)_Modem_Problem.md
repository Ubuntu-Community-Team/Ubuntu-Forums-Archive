---
title: "USRobotics (3Com) Modem Problem"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by EnRock on 2005-07-13
I'm trying to get a PCI-USRobotics Modem (Yes, it is a true hardware modem) working in a G4 with Hoary. Initially the kernels oops'd on bootup, but after recompiling the kernel with the 8250 and serial_core as modules I could get the machine up and running.

Everything looks good with lspci -vv. I see the card, and it has an allocated IO address  (0x1020) and IRQ (53). It is disabled (I/O-), but I understand the serial driver will enable it when it is found. There are no ttyS* devices, but I also understand that these will be automagically created by the driver/udev system when the module has been correctly loaded.

The problem is when I try to "modprobe 8250_pci". I get the following error message:
 
```
WARNING: Error inserting 8250 (/lib/modules/2.6.10enrock.2/kernel/drivers/serial/8250.ko): No such device
FATAL: Error inserting 8250_pci (/lib/modules/2.6.10enrock.2/kernel/drivers/serial/8250_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

The appropriate lines from dmesg are:

```
serial8250_init: nothing to do on PowerMac
8250_pci: Unknown symbol serial8250_unregister_port
8250_pci: Unknown symbol serial8250_resume_port
8250_pci: Unknown symbol serial8250_register_port
8250_pci: Unknown symbol serial8250_suspend_port
```

Which to me appear to be errors due to the fact that the 8250 (a dependancy of 8250_pci) doesn't load. I believe the real problem is the "No Such Device" message issued by the 8250 module. The "serial_core" module (a dependancy of 8250) seems to be correctly loaded as it shows up with a lsmod. I get the same results whether I enable the PCI card (via "setpci -d 12b9:1008 command=1") before the modprobe or not.

I am currently dual-booting this machine with YDL (2.3??), and the modem works fine there. Of course it is using the 2.4.X kernel so I suspect something has changed in the new 2.6.X modules. I will probably try compiling an ubuntu 2.4.X kernel, but ..

**Can anyone help me get this card working with the 2.6.X kernel stream?**

If you need any further details, can correct any of my assumptions, or believe you know of a resource I may not have already read, please let me know.

Thanks in advance for any help.

---

