---
title: "usb mouse keeps disconnecting and reconnecting"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by marcele on 2006-12-14
Everything was fine for a week then suddenly my mouse keeps disconnecting and reconnecting ?

Anyone know how to fix this ? (I'm on edgy 2.6.17-10-generic)

tail -f /var/log/messages

Dec 13 23:49:22 marcel-laptop kernel: [17179995.964000] usb 2-3: USB disconnect, address 11
Dec 13 23:49:23 marcel-laptop kernel: [17179996.268000] usb 2-3: new low speed USB device using ohci_hcd and address 12
Dec 13 23:49:24 marcel-laptop kernel: [17179997.220000] ohci_hcd 0000:00:13.1: wakeup
Dec 13 23:49:24 marcel-laptop kernel: [17179997.604000] usb 2-3: new low speed USB device using ohci_hcd and address 14
Dec 13 23:49:24 marcel-laptop kernel: [17179997.812000] usb 2-3: configuration #1 chosen from 1 choice
Dec 13 23:49:24 marcel-laptop kernel: [17179997.824000] usb 2-3: USB disconnect, address 14
Dec 13 23:49:25 marcel-laptop kernel: [17179998.232000] ohci_hcd 0000:00:13.1: wakeup
Dec 13 23:49:25 marcel-laptop kernel: [17179998.616000] usb 2-3: new low speed USB device using ohci_hcd and address 15
Dec 13 23:49:25 marcel-laptop kernel: [17179998.824000] usb 2-3: configuration #1 chosen from 1 choice
Dec 13 23:49:25 marcel-laptop kernel: [17179998.836000] usb 2-3: USB disconnect, address 15
Dec 13 23:49:26 marcel-laptop kernel: [17179999.240000] ohci_hcd 0000:00:13.1: wakeup
Dec 13 23:49:26 marcel-laptop kernel: [17179999.624000] usb 2-3: new low speed USB device using ohci_hcd and address 16
Dec 13 23:49:26 marcel-laptop kernel: [17179999.832000] usb 2-3: configuration #1 chosen from 1 choice
Dec 13 23:49:26 marcel-laptop kernel: [17179999.844000] usb 2-3: USB disconnect, address 16
Dec 13 23:49:27 marcel-laptop kernel: [17180000.248000] ohci_hcd 0000:00:13.1: wakeup
Dec 13 23:49:27 marcel-laptop kernel: [17180000.632000] usb 2-3: new low speed USB device using ohci_hcd and address 17
Dec 13 23:49:27 marcel-laptop kernel: [17180000.840000] usb 2-3: configuration #1 chosen from 1 choice
Dec 13 23:49:27 marcel-laptop kernel: [17180000.840000] usb 2-3: USB disconnect, address 17
Dec 13 23:49:28 marcel-laptop kernel: [17180001.256000] ohci_hcd 0000:00:13.1: wakeup

---

