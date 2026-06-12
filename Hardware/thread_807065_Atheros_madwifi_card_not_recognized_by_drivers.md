---
title: "Atheros madwifi card not recognized by drivers"
date: 2008-05-25
forum: Hardware
---

### Post by fortran77 on 2008-05-25
I have an atheros wifi pci card that should work with madwifi drivers. It works under other distributions and with ubuntu 7.10. With ubuntu 8.04 the card is listed by lspci:
```
05:05.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```but when I try to load the atheros modules (provided by linux-restricted-modules) I get this error:
```
[11678.988830] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[11681.590052] ath_pci: 0.9.4
[11681.590095] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 20 (level, low) -> IRQ 21
[11681.590125] ath_attach: devid 0x13
[11681.602096] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[11681.602129] ACPI: PCI interrupt for device 0000:05:05.0 disabled
```

Did something changhe in the madwifi drivers? What can I do to get this card to work under ubuntu 8.04?

---

