---
title: "Internal ADSL modem"
date: 2010-06-07
forum: Hardware
---

### Post by awacs on 2010-06-07
I'd like to go internal - kids keep getting to the wires, etc. What might be a good internal ADSL modem to run under ubuntu? I bought an Efficient Networks 3060 on eBay, but I can't even find Windows drivers (or a manual) - let alone Linux drivers.

Thanks!

---

### Post by awacs on 2010-06-11
I happened to buy an ADSL modem the other day on eBay - a SpeedStream 3060 from Efficient Networks. Now, the company's out of business for five years, the co. that bought them doesn't acknowledge knowing them :-) and I can't even find *Windows* drivers - but I figure I'll pop it in (PCI) and hope for the best.

# lspci -v:

02:01.0 ATM network controller: Efficient Networks, Inc SpeedStream (LANAI)
        Subsystem: Efficient Networks, Inc Device 0809
        Flags: bus master, medium devsel, latency 64, IRQ 48
        BIST result: 00
        Memory at fc200000 (32-bit, non-prefetchable) [size=256K]
        [virtual] Expansion ROM at 40020000 [disabled] [size=32K]
        Capabilities: [40] Power Management version 1
        Kernel driver in use: lanai
        Kernel modules: lanai

and lsmod reports:

lanai                  24440  1
atm                    35745  1 lanai

that atm entry looks promising. Can anyone here give advice/suggestions/etc. on how to get this thing into operation?

dmesg:

[   40.572360] lanai: In lanai_dev_open()
[   40.572405]   alloc irq_desc for 48 on node -1
[   40.572413]   alloc kstat_irqs on node -1
[   40.572439] lanai 0000:02:01.0: PCI->APIC IRQ transform: INT A -> IRQ 48
[   40.572460] lanai: PCI says board_id=2, board_rev=1
[   40.572466] lanai: Found PCI board-id 2 -- not a Lanai 25.6
[   40.572570] lanai: lanai_start() failed, err=19
[   40.572823] lanai(itf 0): shutting down interface
[   40.573607] Modules linked in: lanai(+)

The lanai_start() failed doesn't look so good ...

Thanks!

---

### Post by skols on 2012-02-23
Hi, i just bought the same modem for the same reasons and i get the same error.
Did you maybe solve the problem in the meantime? If you did, how did you do it?

---

### Post by awacs on 2012-02-23
> **skols said:**
> Hi, i just bought the same modem for the same reasons and i get the same error.
Did you maybe solve the problem in the meantime? If you did, how did you do it?

Sorry, tossed it.

---

