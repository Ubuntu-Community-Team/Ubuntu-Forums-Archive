---
title: "VIA VT6306 firewire card problem?"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by gibberman on 2008-04-19
I'm sorry if this is a repost, but I wasn't sure which section to paste my problem. :-( Anyway, I just inserted a VIA VT6306 into an open PCI slot this morning, and I was wondering if the thing was even detected. I typed in:

[I]
lspci –vvv |more
[/I]
and got:

[I]03:09.0 FireWire (IEEE 1394): Unknown device 0106:3044 (rev 46) (prog-if 00 [Gen
eric])
        Subsystem: Unknown device 0106:3044[/I]


Shouldn't I be seeing:

[I]FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394...[OHCI]
Subsystem: VIA Technologies, Inc.  IEEE 1394 Host Controller[/I]


thanks in advance guys.

---

