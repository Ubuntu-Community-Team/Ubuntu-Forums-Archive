---
title: "ATT Sierra AirCard 875 PCMCIA - fails to install USB  &quot;takeover failed!&quot;"
date: 2009-04-10
forum: Hardware
---

### Post by hanasaki on 2009-04-10
ATT Sierra AirCard 875 PCMCIA - fails to install USB  "takeover failed!"

Trying to get this card working however getting the below errors when inserting the card in the laptop.  lsusb also fails to show the card.

This is on jaunty with the stock kernel.
Linux laptop 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:39:23 UTC 2009 x86_64 GNU/Linux

Apr  9 17:00:41 laptop kernel: [  674.172167] ohci_hcd 0000:04:00.0: USB HC takeover failed!  (BIOS/SMM bug)
Apr  9 17:00:41 laptop kernel: [  674.172177] ohci_hcd 0000:04:00.0: can't setup
Apr  9 17:00:41 laptop kernel: [  674.172186] ohci_hcd 0000:04:00.0: USB bus 8 deregistered
Apr  9 17:00:41 laptop kernel: [  674.174861] ohci_hcd 0000:04:00.0: PCI INT A disabled
Apr  9 17:00:41 laptop kernel: [  674.174869] ohci_hcd 0000:04:00.0: init 0000:04:00.0 fail, -16
Apr  9 17:00:41 laptop kernel: [  674.175008] ohci_hcd: probe of 0000:04:00.0 failed with error -16
Apr  9 17:00:41 laptop kernel: [  674.175206] ohci_hcd 0000:04:00.1: enabling device (0000 -> 0002)
Apr  9 17:00:41 laptop kernel: [  674.175219] ohci_hcd 0000:04:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  9 17:00:41 laptop kernel: [  674.175283] ohci_hcd 0000:04:00.1: setting latency timer to 64
Apr  9 17:00:41 laptop kernel: [  674.175291] ohci_hcd 0000:04:00.1: OHCI Host Controller
Apr  9 17:00:41 laptop kernel: [  674.175448] ohci_hcd 0000:04:00.1: new USB bus registered, assigned bus number 8
Apr  9 17:00:49 laptop kernel: [  682.188189] ohci_hcd 0000:04:00.1: USB HC takeover failed!  (BIOS/SMM bug)
Apr  9 17:00:49 laptop kernel: [  682.188199] ohci_hcd 0000:04:00.1: can't setup
Apr  9 17:00:49 laptop kernel: [  682.188208] ohci_hcd 0000:04:00.1: USB bus 8 deregistered
Apr  9 17:00:49 laptop kernel: [  682.190489] ohci_hcd 0000:04:00.1: PCI INT B disabled
Apr  9 17:00:49 laptop kernel: [  682.190496] ohci_hcd 0000:04:00.1: init 0000:04:00.1 fail, -16
Apr  9 17:00:49 laptop kernel: [  682.190515] ohci_hcd: probe of 0000:04:00.1 failed with error -16

---

