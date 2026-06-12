---
title: "wrong MAC-address dmesg shows"
date: 2009-01-06
forum: Hardware
---

### Post by GenuAliEn on 2009-01-06
Hi All!
I'm sorry if I have mistakes in my post, just I don't write good English.
OS: Ubuntu 8.04, kernel 2.6.24

This is my trouble. I does all correct for do my SkyStar2 DVB-card working, it receiving signal but dvbtraffic shows nothing and dmesg shows wrong MAC:
> [   37.098023] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   37.159354] flexcop-pci: will use the HW PID filter.
[   37.159365] flexcop-pci: card revision 2
[   37.159384] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 20
[   37.174026] DVB: registering new adapter (FlexCop Digital TV device)
**[   37.175869] b2c2-flexcop: MAC address = 00:d0:d7:0e:3f:2d**
[   37.849270] b2c2-flexcop: found the stv0299 at i2c address: 0x68
[   37.849278] DVB: registering frontend 0 (ST STV0299 DVB-S)...
[   37.849346] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
Really my MAC is 00:d0:d7:02:04:c9. I try to redefine MAC by ifconfig but it also don't solve the problem.
My card is working successfuly, I use it on Windows.
Thanks for any help.

---

