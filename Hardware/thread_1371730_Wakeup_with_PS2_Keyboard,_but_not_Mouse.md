---
title: "Wakeup with PS/2 Keyboard, but not Mouse?"
date: 2010-01-03
forum: Hardware
---

### Post by jrcdude on 2010-01-03
So I have successfully managed to make Ubuntu wakeup from suspend by doing the following commands:

```
root@jason-desktop:~# cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
HUB0	  S5	 disabled  pci:0000:00:04.0
XVR0	  S5	 disabled  pci:0000:00:09.0
XVR1	  S5	 disabled  pci:0000:00:0b.0
XVR2	  S5	 disabled  pci:0000:00:0c.0
PS2M	  S4	 disabled  pnp:00:08
PS2K	  S4	 disabled  pnp:00:09
USB0	  S3	 disabled  pci:0000:00:02.0
USB2	  S3	 disabled  pci:0000:00:02.1
AZAD	  S5	 disabled  
MMAC	  S5	 disabled  pci:0000:00:07.0
root@jason-desktop:~# echo "PS2K" > /proc/acpi/wakeup
root@jason-desktop:~# cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
HUB0	  S5	 disabled  pci:0000:00:04.0
XVR0	  S5	 disabled  pci:0000:00:09.0
XVR1	  S5	 disabled  pci:0000:00:0b.0
XVR2	  S5	 disabled  pci:0000:00:0c.0
**PS2M	  S4	 enabled   pnp:00:08**
PS2K	  S4	 enabled   pnp:00:09
USB0	  S3	 disabled  pci:0000:00:02.0
USB2	  S3	 disabled  pci:0000:00:02.1
AZAD	  S5	 disabled  
MMAC	  S5	 disabled  pci:0000:00:07.0

```

but as you can see (bolded) the PS2M has automatically been enabled as well, is there a way to enable only one so that a slight movement of the mouse will not wake up the computer?

Thanks,
Jason.

---

