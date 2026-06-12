---
title: "HP printer does no longer work with PCMCIA- / CardBus-enabled parallel port"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by Ewlcsg on 2008-01-30
Hello,

I have a HP Deskjet 690C parallel port printer which I will use on a Lenovo 3000 N100 Laptop (which does work mostly very fine with Ubuntu). Because the Laptop does not have a parallel port, I did buy a PCMCIA / CardBus adapter card which identifies itself after inserting in /var/log/messages as follow:

```
... NET: Registered protocol family 10
... lo: Disabled Privacy Extensions
... pccard: CardBus card inserted into slot 0
... yenta EnE: chaning testregister 0xC9, 04 -> 04
... PCI: Enabling device 0000:06:00.0 (0000 -> 0003)
... ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 16 (level, low) -> IRQ 17
... parport0: PC-style at 0x2420 [PCSPP]
... lp0: using parport0 (polling).
...] ppdev: user-space parallel port driver
... audit(1201744433.760:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5897 profile="/usr/sbin/cupsd"

```

Exactly this hardware configuration did work fine with CUPS with an early version of Ubuntu 6.06 LTS.
Unfortunately this version of Ubuntu did not support my UMTS modem, so I had to switch to the upcoming 6.10 version. Now UMTS did work fine, but the printer did stop working: After some noise, the printer did simple nothing. So I was in doubt if my hardware is defekt.

Done to some other problem recently I did reinstall the entire laptop - this time with Ubuntu 7.10 (fully updated until today). Now the printer does work again - but while trying to print a test page, resulting  output is mostly garbage (along with some part of the real testpage).

Does anybody here have any idea what to do to get the printer working right?
Thanks for any hint!

Here is some more information:

```
root@csg-laptop:~# lspcmcia -v
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:05:04.0)
        Configuration:  state: on       ready: yes
                        Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V
  CardBus card -- see "lspci" for more information
root@csg-laptop:~# 

```

```
root@csg-laptop:~# lspci -v
[...]
06:00.0 Parallel controller: Oxford Semiconductor Ltd VScom 011H-EP1 1 port parallel adaptor (prog-if 03 [IEEE1284])
        Subsystem: Oxford Semiconductor Ltd Unknown device 0000
        Flags: medium devsel, IRQ 17
        I/O ports at 2420 [size=8]
        I/O ports at 2428 [size=4]
        I/O ports at 2400 [size=32]
        Memory at 54000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 1

```

---

