---
title: "Hoary's not seeing USB/Firewire"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by vrl2 on 2005-08-23
Hello,

I am having trouble getting Linux to recognize the following card:
Syba SD-PCB-COM
Chipset: M5271
Product Info: [http://www.syba.com/product/43/05/01/](http://www.syba.com/product/43/05/01/)
It offers 2 USB2 ports and 2 firewire ports.

When I insert it and run 'cardctl ident 0' [when this card is plugged
into slot 0] I am given the message "no product info available."  The
system has no trouble, however, recognizing my wireless PCMCIA card
[linksys wpc11].

I have additionally tried running "lspci" and "pcimodules" and these respond to the card being inserted:

~# lspci
0000:02:00.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:00.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:00.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:02:00.4 FireWire (IEEE 1394): ALi Corporation M5253 P1394 OHCI 1.1 Controller

~# pcimodules
ohci-hcd
ehci-hcd
ohci1394

Included at the bottom of the email is information that Ksysteminfo reports under "USB DEVICES".  Also, the device seems to have consequences in the PCMCIA section of system info.  While Ubuntu seems to recognize that there are extra USB ports available, it cannot recognize any devices attached to these ports...

What could be the trouble?  The card not only refuses to be
recognized, but when I insert it it actually prevents the
otherwise-functional wireless internet card from being recognized as
well.  There are windows and mac drivers available for this
troublesome SD-PCB-COM, but unfortunately I'm unsure about how to make
it work under Linux.  Is it possible to use the windows drivers to
construct a driver for linux?

I'm running the latest version of Ubuntu.  My computer is a IBM
Thinkpad A21m. If anyone can think of any possible solutions, I'd love
to hear them Please contact me at [email]venkat@aya.yale.edu[/email] with any
suggestions.  I apprecaite it!

Venkat
----------
Intel Corp. 82371AB/EB/MB PIIX4 USB (4)
Manufacturer: Linux 2.6.10-5-386 uhci_hcd
Serial #: 0000:00:07.2

ALi Corporation USB 2.0 Controller (1)
Manufacturer: Linux 2.6.10-5-386 ehci_hcd
Serial #: 0000:02:00.3

ALi Corporation USB 1.1 Controller (#2) (3)
Manufacturer: Linux 2.6.10-5-386 ohci_hcd
Serial #: 0000:02:00.1

ALi Corporation USB 1.1 Controller (2)
Manufacturer: Linux 2.6.10-5-386 ohci_hcd
Serial #: 0000:02:00.0

---

000:02:00.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
Subsystem: Ali Corporation: Unknown device 5272
Flags: bus master, 66MHz, medium devsel, latency 16, IRQ 11
Memory at 10400000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [60] Power Management version 2

000:02:00.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
Subsystem: Ali Corporation: Unknown device 5272
Flags: bus master, 66MHz, medium devsel, latency 16, IRQ 11
Memory at 10401000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [60] Power Management version 2

000:02:00.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
Subsystem: Ali Corporation: Unknown device 5272
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
Memory at 10402800 (32-bit, non-prefetchable) [size=256K]
Capabilities: [50] Power Management version 2
Capabilities: [58] #0a [2090]

000:02:00.4 FireWire (IEEE 1394): ALi Corporation M5253 P1394 OHCI 1.1 Controller (prog-if 10 [OHCI])
Subsystem: Ali Corporation: M5253 P1394 OHCI 1.1 Controller
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
Memory at 10402000 (32-bit, non-prefetchable) [size=64K]
Capabilities: [80] Power Management version 2

---

