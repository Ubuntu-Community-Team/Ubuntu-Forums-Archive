---
title: "USB keyboard / hotplugging"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by mlho on 2006-06-05
Upgraded from Breezy to Dapper on my Toshiba Satellite 1800 laptop.

USB keyboard worked fine with Breezy, but stopped working since upgrade. Works at the Grub menu and in Windows dual boot partition. But stops working once I hit the Ubuntu log-in screen.

Other people have had similar problems (see [http://www.ubuntuforums.org/showthread.php?t=186174)](http://www.ubuntuforums.org/showthread.php?t=186174)), [http://ubuntuforums.org/showthread.php?t=186689](http://ubuntuforums.org/showthread.php?t=186689) and [http://ubuntuforums.org/showthread.php?t=187896)](http://ubuntuforums.org/showthread.php?t=187896)). 

But, the solution suggested in these threads doesn't work for me (i.e. turning of BIOS USB legacy support makes no difference).

Also, the hot-plugging doesn't seem to work anymore. So disconnecting and reconnect my USB mouse causes it to stop working.

**lsusb** gives:
[INDENT]Bus 002 Device 002: ID 0483:f001 SGS Thomson Microelectronics
Bus 002 Device 003: ID 062a:0201 Creative Labs
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0603:7132 Novatek Microelectronics Corp.
Bus 001 Device 001: ID 0000:0000[/INDENT]

The keyboard is the Novatek device.

**dmesg |grep usb** gives several screen fulls of this (i.e. several hundred lines of the same thing):
[INDENT][4340359.437000] drivers/usb/input/hid-core.c: input irq status -32 received
[4340359.437000] drivers/usb/input/hid-core.c: input irq status -32 received
[4340359.445000] drivers/usb/input/hid-core.c: input irq status -32 received
[INDENT]:
:
[/INDENT][4340360.309000] drivers/usb/input/hid-core.c: input irq status -32 received
[4340360.317000] drivers/usb/input/hid-core.c: input irq status -32 received
[4340360.317000] drivers/usb/input/hid-core.c: input irq status -32 received[/INDENT]

Any ideas or how to get the keyboard working again?

Mark

---

### Post by marquisdesade on 2006-09-28
> **mlho said:**
> Upgraded from Breezy to Dapper on my Toshiba Satellite 1800 laptop.

USB keyboard worked fine with Breezy, but stopped working since upgrade. Works at the Grub menu and in Windows dual boot partition. But stops working once I hit the Ubuntu log-in screen.

Other people have had similar problems (see [http://www.ubuntuforums.org/showthread.php?t=186174)](http://www.ubuntuforums.org/showthread.php?t=186174)), [http://ubuntuforums.org/showthread.php?t=186689](http://ubuntuforums.org/showthread.php?t=186689) and [http://ubuntuforums.org/showthread.php?t=187896)](http://ubuntuforums.org/showthread.php?t=187896)). 

But, the solution suggested in these threads doesn't work for me (i.e. turning of BIOS USB legacy support makes no difference).

Also, the hot-plugging doesn't seem to work anymore. So disconnecting and reconnect my USB mouse causes it to stop working.



I'm facing the same problems too. I upgraded yesterday to 2.6.15-27, and USB keyboard/mouse dont work anymore. I have Dell Inspiron 600m, Centrino 1.6Ghz. Keyboard is a dell and mouse is a logitech.

> 

**lsusb** gives:
[INDENT]Bus 002 Device 002: ID 0483:f001 SGS Thomson Microelectronics
Bus 002 Device 003: ID 062a:0201 Creative Labs
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0603:7132 Novatek Microelectronics Corp.
Bus 001 Device 001: ID 0000:0000[/INDENT]

The keyboard is the Novatek device.

**dmesg |grep usb** gives several screen fulls of this (i.e. several hundred lines of the same thing):
[INDENT][4340359.437000] drivers/usb/input/hid-core.c: input irq status -32 received
[4340359.437000] drivers/usb/input/hid-core.c: input irq status -32 received
[4340359.445000] drivers/usb/input/hid-core.c: input irq status -32 received
[INDENT]:
:
[/INDENT][4340360.309000] drivers/usb/input/hid-core.c: input irq status -32 received
[4340360.317000] drivers/usb/input/hid-core.c: input irq status -32 received
[4340360.317000] drivers/usb/input/hid-core.c: input irq status -32 received[/INDENT]

Any ideas or how to get the keyboard working again?



Yes, please... this does not look like a random occurrence to me

---

