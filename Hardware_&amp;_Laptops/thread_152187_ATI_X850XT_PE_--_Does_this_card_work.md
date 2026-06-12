---
title: "ATI X850XT PE -- Does this card work ??"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by tebbens on 2006-03-29
Before an HD installed I've tried the Live Breezy & Dapper CD with no luck.
Does anyone have this card working with Breezy and/or Dapper ?

lspci -v
0000:01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 0302
        Flags: fast devsel, IRQ 11
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at efde0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at dc00 [size=256]
        Expansion ROM at efe00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #10 [0001]
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

0000:01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (Secondary)
        Subsystem: ATI Technologies Inc: Unknown device 0303
        Flags: bus master, fast devsel, latency 0
        Memory at efdf0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #10 [0001]

lspci -n
0000:01:00.0 0300: 1002:5d4d
0000:01:00.1 0380: 1002:5d6d

Does (PCIE) mean PCI Enhanced, and also that there is no driver available ?

Thanks !
Matthew

---

### Post by encompass on 2006-03-29
Goodness.. I like your card... it should work... I would look up the fglrx driver install... in the forums... ask and search there for an answer.
ATI is in my opinion not the best card for linux... but it works... I use ati.
PS and PCIE is PCI express it is the step faster then AGP

---

