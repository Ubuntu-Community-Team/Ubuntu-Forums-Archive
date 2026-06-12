---
title: "HP G4 USB-C Dock and DisplayLink"
date: 2019-10-17
forum: Hardware
---

### Post by tom.k.cook on 2019-10-17
I have an HP G4 USB-C dock that has two DisplayPort and one HDMI outputs.  It also has USB ports and Ethernet, which work, but the display outputs don't.  I'm running the 19.10 beta.

I thought this was a DisplayLink device so I installed the DisplayLink Ubuntu drivers.  But the device doesn't show up in lsusb:

```
$ lsusb -d 17e9:
$
```

The things that do show up in the full lsusb output when I plug the dock in are:

```
0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
04b4:6504 Cypress Semiconductor Corp.
04b4:6504 Cypress Semiconductor Corp.
03f0:484a HP, Inc
0bda:482a Realtek Semiconductor Corp.
04b4:6572 Cypress Semiconductor Corp.
04b4:6506 Cypress Semiconductor Corp. CY4603
04b4:6506 Cypress Semiconductor Corp. CY4603
```

The issue seems to be that 04b4:6504 is a USB 3 hub that is not being recognized / supported.  I'm guessing that the DisplayLink devices are behind this hub.

Is there a way to enable support for this hub?

**Edit:**  Scratch that, ```
lsusb -t
``` shows that the hub is working fine.  But there are still no dislay-link devices shown.  It's looking likely that `03f0:484a` is some HP-specific code for a USB display device, though finding out what might be difficult.  Is there a way to force an attempt to connect the displaylink driver to this device?

---

