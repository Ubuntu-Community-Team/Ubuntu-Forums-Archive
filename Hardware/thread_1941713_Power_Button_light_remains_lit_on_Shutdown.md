---
title: "Power Button light remains lit on Shutdown"
date: 2012-03-16
forum: Hardware
---

### Post by ru55377 on 2012-03-16
This issue is present on installed and Live CD versions 9.04, 11.04 and 11.10 - though it could be present on others but I haven't tested these.

When the PC is shutdown, initiated using either the menu option or the power button the PC does shutdown, it is possible to hear the fans and the disks stop. However the power button remains constantly lit - nice bright blue LED. Press the power button and the PC starts normally, not from suspend or hibernate.

As the USB power retains power on shutdown thought it might be related to this, so had the USB power down on shutdown by issuing the command: 
```
modprobe -r -v whci_hcd
```The USB ports do power down on shutdown, however the power button light remains lit.

Running Windows XP on the same PC, initiate a shutdown and everthing powers itself off, including the power button light.

The motherboard is a ASUS P8H61-MX, cannot find anything in the BIOS that is related to this issue. Any help would be appreciated.

---

### Post by ru55377 on 2012-03-16
Have tried the kernel options;

```
acpi=force
```Have in-additional also used the details found at [http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/ ]("http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/")

So the kernel parameters would look something like;

```
acpi=force reboot=bios
```Have tried all the reboot options with and without the acpi=force option, still no joy, the power button light remains stubbornly on. Haven't tried all the multiple combinations of reboot, i.e.

```
reboot=force,bios,efi
```etc. Not sure it will make any difference as the PC does shutdown, just the power button light remains on.

---

### Post by rcolquhoun on 2012-06-25
I am also experiencing the exact same problem. 
 
Using a ASUS P8H61-MX mobo running Ubuntu 10.04 LTS.
 
Certainly seems like a mobo compatability issue. If anyone has any suggestions I'd be much appreciative.

---

