---
title: "No USB 2.0 on Acer Travelmate 4000LMi"
date: 2004-12-31
forum: Hardware &amp; Laptops
---

### Post by thtde on 2004-12-31
Hello,

I've installed Ubuntu on my notebook. But I can't use usb 2.0 high speed mode (full speed works without problems).

dmesg|grep ehci
```
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller
ehci_hcd 0000:00:1d.7: irq 10, pci mem df931000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:1d.7: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
ehci_hcd 0000:00:1d.7: fatal error
ehci_hcd 0000:00:1d.7: HC died; cleaning up
``` 

I've tested this with the latest kernels in Warty and in Hoary (2.6.10).

---

### Post by thtde on 2005-01-02
a longer part from dmesg```
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 6 (level, low) -> IRQ 6
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB (ICH4) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 6, io base 00001820
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 6 (level, low) -> IRQ 6
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB (ICH4) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 6, io base 00001840
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 6 (level, low) -> IRQ 6
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB (ICH4) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 6, io base 00001860
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
hub 1-0:1.0: over-current change on port 1
hub 1-0:1.0: over-current change on port 2
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 10 (level, low) -> IRQ 10
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 10, pci mem dfa08000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
ehci_hcd 0000:00:1d.7: fatal error
ehci_hcd 0000:00:1d.7: HC died; cleaning up
``` 

I often get the message "usb usb4: string descriptor 0 read error: -19".

---

### Post by snop on 2005-01-02
Hi,

Same here. I always get this "usb usb4: string descriptor 0 read error: -19" message. I didn't realized that usb wasn't working at high speed (although I saw that photos were transmitted from my camera to the computer at low speeds).

I own an Acer 4001Wlmi (basicaly the same as yours). The message is also present when using 2.6.10.

Bye

PD: Perhaps we should fill a bug report...

---

### Post by thtde on 2005-01-03
[QUOTE=snop]PD: Perhaps we should fill a bug report...[/QUOTE]

Done. See [https://bugzilla.ubuntu.com/show_bug.cgi?id=5153](https://bugzilla.ubuntu.com/show_bug.cgi?id=5153)

---

