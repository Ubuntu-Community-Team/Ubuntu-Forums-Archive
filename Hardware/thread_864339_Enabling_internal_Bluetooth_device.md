---
title: "Enabling internal Bluetooth device"
date: 2008-07-19
forum: Hardware
---

### Post by MasterOfNothing on 2008-07-19
Hi!

I have just bought a new laptop which has a built-in CSR USB bluetooth device.

The problem is that it is not listed if I run "lsusb" and after looking at the windows drivers supplied for it with the laptop, I see that it actually is a Toshiba driver (and therefore uses the Toshiba bluetooth stack).

Toshutils and the toshiba acpi kernel driver should implement handling of such bluetooth devices (in short, those are detached and powered off at boot, but can be enabled by a hardware call). The problem is that my laptop is not a toshiba (consequently toshiba_acpi.ko does not work).

Is there any way of turning the power on and attaching the device in my situation?

Thanks in advance! Any kind of help is highly appreciated.

---

