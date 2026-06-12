---
title: "Trying to get HP iPaq Pocket PC working with Ubuntu"
date: 2008-11-08
forum: General Help
---

### Post by ubnewbie2 on 2008-11-08
When I plug my HP iPaq Pocket PC into my usb port, I see the following with dmesg

```
[ 7192.612018] usb 4-6: new high speed USB device using ehci_hcd and address 2
[ 7192.746378] usb 4-6: configuration #1 chosen from 1 choice
[ 7192.881641] usbcore: registered new interface driver cdc_ether
[ 7193.119531] rndis_host 4-6:1.0: RNDIS_MSG_QUERY(0x00010202) failed, -47
[ 7193.121484] eth1: register 'rndis_host' at usb-0000:00:04.1-6, RNDIS device, 80:00:60:0f:e8:00
[ 7193.121512] usbcore: registered new interface driver rndis_host
[ 7193.148368] usbcore: registered new interface driver rndis_wlan
[ 7207.756014] eth1: no IPv6 routers present

```

What do I need to do next?  I would like to be able to access the memory in the iPaq mounted like an external drive, and also be able to synchronise some data, and backup some data.

Edit:  I have 8.10 installed

---

