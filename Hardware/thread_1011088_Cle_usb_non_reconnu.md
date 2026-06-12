---
title: "Cle usb non reconnu"
date: 2008-12-14
forum: Hardware
---

### Post by marco123! on 2008-12-14
Materiel : ASUS Z92J

SI je boote avec cle usb : elle est reconnu , son device est crée
SI je boote , puis j'insere la cle usb -> rien , impossible de monter la clé usb

Avez vous une idée ( montage automatique à activer ou autre piste )
Note : lsusb : la cle n'apparait pas )

/var/log/message

Dec 14 12:10:32 bayle kernel: [    2.743213] usbcore: registered new interface driver usbfs
Dec 14 12:10:32 bayle kernel: [    2.743242] usbcore: registered new interface driver hub
Dec 14 12:10:32 bayle kernel: [    2.776232] usbcore: registered new device driver usb
Dec 14 12:10:32 bayle kernel: [    2.827009] USB Universal Host Controller Interface driver v3.0
Dec 14 12:10:32 bayle kernel: [    2.827077] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 14 12:10:32 bayle kernel: [    2.827093] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 14 12:10:32 bayle kernel: [    2.827142] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Dec 14 12:10:32 bayle kernel: [    2.827180] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ec00
Dec 14 12:10:32 bayle kernel: [    2.827358] usb usb1: configuration #1 chosen from 1 choice
Dec 14 12:10:32 bayle kernel: [    2.827391] hub 1-0:1.0: USB hub found
Dec 14 12:10:32 bayle kernel: [    2.827399] hub 1-0:1.0: 2 ports detected
Dec 14 12:10:32 bayle kernel: [    2.836986] No dock devices found.
Dec 14 12:10:32 bayle kernel: [    2.854127] SCSI subsystem initialized
Dec 14 12:10:32 bayle kernel: [    2.929349] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 14 12:10:32 bayle kernel: [    2.929366] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 14 12:10:32 bayle kernel: [    2.929398] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Dec 14 12:10:32 bayle kernel: [    2.929436] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e880
 Pareil pour usb2,usb3,usb4

---

