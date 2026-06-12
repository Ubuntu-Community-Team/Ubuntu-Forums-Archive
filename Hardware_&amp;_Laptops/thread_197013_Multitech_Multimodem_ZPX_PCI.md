---
title: "Multitech Multimodem ZPX PCI"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by DaudDaud on 2006-06-15
HI:

I'd appreciate a few pointers, as I'm new to Ubuntu. (6.06 i386 on a Pentium D)

The install misidentified my modem (Multitech Multimodem ZPX PCI MT5634ZPX-PCI-U-GB) as an Agere Systems Venus Modem (V90, 56KFlex) (unless of course they're the same chip ??) and says its on ttyS4.  SUSE 10.1 (dual boot) identifies the card correctly (and says it's on ttyS0) - and it works there.  I need the modem only for faxing (I have cable broadband for internet etc. access) and conceivably some telephony at a future date.

Output of lspci -v is:

0000:00:0b.0 Communication controller: Agere Systems Venus Modem (V90, 56KFlex)
        Subsystem: Agere Systems: Unknown device 5656
        Flags: bus master, medium devsel, latency 0, IRQ 169
        Memory at f9eff400 (32-bit, non-prefetchable) [size=256]
        I/O ports at e400 [size=256]
        I/O ports at e000 [size=256]
        I/O ports at e800 [size=8]
        Capabilities: [f8] Power Management version 2

(What on earth is IRQ 169?)

My question, though, is (I hope) straightforward - how do I go about setting up the system correctly in Ubuntu and telling it what is where?

I'd be pleased to provide any further info you may need & would be grateful for any pointers ....

Thanks

D2

---

