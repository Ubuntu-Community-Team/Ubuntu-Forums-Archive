---
title: "wifi disconnects"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by aspak on 2005-07-06
I'm running kernel v. 2.6.10 on a dell inspiron 510m, with intel centrino card. I'm having some issues with my wifi, everything works fine when I boot, wifi works, but after some time (5-10 minutes) it disconnects. I then have to do rmmod ipw2200 and modprobe ipw2200, and the card works fine again, ie it does not disconnect again.
These are the last lines from dmesg:

ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:1d.0 to 64
PCI: Setting latency timer of device 0000:00:1d.1 to 64
PCI: Setting latency timer of device 0000:00:1d.2 to 64
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 restarted, EHCI 1.00, driver 26 Oct 2004
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:00:1f.5 to 64
ACPI: PCI interrupt 0000:01:01.1[B] -> GSI 11 (level, low) -> IRQ 11
eth0: Coming out of suspend...
ACPI: PCI interrupt 0000:01:03.0[A] -> GSI 5 (level, low) -> IRQ 5
Restarting tasks... done
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:01:03.0[A] -> GSI 5 (level, low) -> IRQ 5
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Fatal error
ipw2200: Start IPW Error Log Dump:
ipw2200: Status: 0x00000100, Config: 00000142
ipw2200: Start IPW Event Log Dump:
eth0: no IPv6 routers present

---

### Post by brim4brim on 2005-07-06
Hi, I had this problem if you upload to the very latest drivers it goes away. 

 If you need a walkthrough on how to install it do a search for ipw2200 using the search button at the top of the page and it'll pop right up.

---

### Post by aspak on 2005-07-07
Thanks, that solved the problem!

---

