---
title: "Dual-channel sync/async serial adapters for PCI or PCIe?"
date: 2017-01-10
forum: Hardware
---

### Post by bcschmerker on 2017-01-10
On the Hot Rod gPC. I plan on experimenting with an external modem; but the only PCI and PCIe multichannel serial adapters I have encountered, as of January 2017, are all for DE-9 hardware connections, rather than the full DB-25 that I'm after.  The terminal via DE-9 (/dev/ttyS0) will be satisfactory (Send Data, Receive Data, Request to Send, Clear to Send, Terminal Ready, and Receiver Ready are sufficient for hookup to the Boundless® VT-5xx or equivalent); but for the modem via /dev/ttyS1 I need subchannels /dev/ttyS1a and /dev/ttyS1b (each having independent Send Data, Receive Data, Request to Send, Clear to Send, and Carrier Detect), with common Terminal Ready, Receiver Ready, Incoming Call, Send Timing, Receive Timing, and Terminal Timing.  What modem boards, if any, satisfy the two-channels-on-one-DB25 requirement and can be provided with a suitable 64-bit driver (including provisions for a level-sensitive IRQ 3)?

---

