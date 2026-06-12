---
title: "serial port /dev/ttyS0 does not work"
date: 2008-11-04
forum: Hardware
---

### Post by cnwesleywang on 2008-11-04
Hi all,I have an old laptop TOSHIBA-SP6100 which has both ubuntu 8.04 and WinXp. I connected this laptop's serial port with another Winxp's serial port.

Under winxp, with both side configured as com1,baud 38400, the serial port communicate with another Winxp is just fine,  but under ubuntu,I use minicom with ttyS0 to do same thing, no any error message come but the other side can receive nothing.

Same thing happened in my IBM x3250 M2 server.

I do google and found someone said there is a bug in kernel 2.6.24-19,dead loop or something and has been fixed in 2.6.27, so I upgrade the kernel of my ubuntu 8.04 to 2.6.27(just get it from ubuntu 8.10),but still no luck.

Can anybody help me to analyze?

uname -r:
   2.6.27-7-generic

dmesg:

......
[    1.806142] isapnp: Scanning for PnP cards...
[    2.159320] isapnp: No Plug & Play device found
[    2.244655] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.244849] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.246414] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.246913] serial 0000:00:1f.6: power state changed by ACPI to D0
[    2.246925] serial 0000:00:1f.6: enabling device (0000 -> 0001)
[    2.246938] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    2.246949] serial 0000:00:1f.6: PCI INT B disabled
[    2.250733] brd: module loaded
[    2.250884] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.251150] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.256716] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.256737] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.257623] mice: PS/2 mouse device common for all mice
......

---

### Post by cnwesleywang on 2008-11-05
After blacklist the smsc-ircc2 module, ttyS0 works just fine.

refer to [http://lkml.org/lkml/2006/11/21/90](http://lkml.org/lkml/2006/11/21/90)

---

### Post by vk4ebp on 2008-11-09
This might be the answer to my problem too (see related thread). Pardon my ignorance but what does blacklisting means and how do I go about it. Newbie here.

---

