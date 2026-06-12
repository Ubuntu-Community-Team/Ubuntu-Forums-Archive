---
title: "Recommendations on a serial terminal, please!"
date: 2009-05-10
forum: Hardware
---

### Post by bcschmerker on 2009-05-10
I am currently preparing for a partial reconfiguration of my Everex mid-tower ([Elitegroup GeForce6100SM-M](http://www.ecsusa.com/) with [Advanced Micro Devices Athlon X2 5600+](http://www.amd.com/)).  The new motherboard already has an immediately-accessible EIA-232D port, /dev/ttyS0, which I'd like to use for monitoring the kernel from without GNOME and GDM (which, along with an X.org server, use the planar [nVIDIA GeForce6100](http://www.nvidia.com/) GPU).  Physical depth (for an 80x25-character unit), cost and power consumption are factors; a plug-in keyboard is a plus, as I don't expect to use the terminal as my primary input device.

---

### Post by andrewc6l on 2009-05-11
Instead of a serial terminal, have you thought about an Ethernet serial port server? They go for around $300, and would let you telnet into your serial port from anywhere, rather than having a dedicated console.

---

### Post by bcschmerker on 2009-05-12
> **andrewc6l said:**
> Instead of a serial terminal, have you thought about an Ethernet serial port server? They go for around $300, and would let you telnet into your serial port from anywhere, rather than having a dedicated console.The task here is basic kernel monitoring rather than a multiple-Console interface for a ready server; setting up an Ethernet serial port server would not be ideal for kernel monitoring, as the kernel data would be unavailable during the boot process.  The monitoring that I have to do starts before an X server would be called up under normal circumstances.

Planar serial-port controls for the National Semiconductor NS16x50J/N have been integrated into the Kernel for some time, while Ethernet adapters are normally linked into the Kernel as Modules.

---

### Post by andrewc6l on 2009-05-16
The Ethernet serial port servers I'm talking about are actual physical hardware, not processes running on the kernel machine. They have a DB-9 connector on one side and an RJ-45 on the other. You can telnet to them, and they relay what comes in on the DB-9 to the RJ-45 and vice versa. You would be able to pick up even BIOS serial port messages from them, let alone kernel boot messages.

---

