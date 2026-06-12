---
title: "An efax/modem problem"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by einpoklum on 2006-01-01
I've been trying to use efax (via kdeprintfax, but that's not relevant), and I've been getting the following:


[FONT="Courier New"]efax: Sun Jan  1 19:55:20 2006 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 55:20 opened /dev/ttyS0

efax: 55:26 sync: dropping DTR
efax: 55:31 sync: sending escapes
efax: 55:36 Error: sync: modem not responding
efax: 55:36 failed -> /tmp/kde-root/kprinter_16751.001
efax: 55:36 done, returning 4 (no response from modem)[/FONT]

and the same for using ttyS1.

My modem, as reported by lspci is:

[FONT="Courier New"]0000:01:06.0 Communication controller: Conexant HCF 56k Data/Fax/Voice Modem (rev 08)[/FONT]

and dmesg | grep tty says:

[FONT="Courier New"][17179572.540000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.540000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A[/FONT]

I'm not sure myself whether my modem is on COM1 or COM2, but like I said, both don't seem to work for me. Any advice?

---

