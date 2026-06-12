---
title: "USB devises not working on Fujitsu Siemens Amilo L7310GW"
date: 2009-04-01
forum: Hardware
---

### Post by Marc Hoffman on 2009-04-01
I have had to hack round to get Ubuntu working on this laptop. I have got wireless working and the correct screen resolution but at the expense of being able to use USB devices. On inserting a drive I get the following output from dmesg | tail

davey@davey-laptop:~$ dmesg | tail
[  150.595601] ath0: no IPv6 routers present
[ 2255.109664] [drm:via_cmdbuf_wait] *ERROR* via_cmdbuf_wait timed out hw 2df60 cur_addr 308 next_addr 80508
[ 2515.096326] usb 4-3: new high speed USB device using ehci_hcd and address 6
[ 2530.629940] usb 4-3: device not accepting address 6, error -110
[ 2530.740598] usb 4-3: new high speed USB device using ehci_hcd and address 7
[ 2546.273011] usb 4-3: device not accepting address 7, error -110
[ 2546.384863] usb 4-3: new high speed USB device using ehci_hcd and address 8
[ 2556.805041] usb 4-3: device not accepting address 8, error -110
[ 2556.916871] usb 4-3: new high speed USB device using ehci_hcd and address 9
[ 2567.335871] usb 4-3: device not accepting address 9, error -110

Also get this ouput

davey@davey-laptop:~$ tail -f /var/log/messages
Apr  1 10:46:27 davey-laptop kernel: [  131.575225] NET: Registered protocol family 17
Apr  1 10:46:35 davey-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Apr  1 10:46:35 davey-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Apr  1 10:46:35 davey-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
Apr  1 11:05:19 davey-laptop -- MARK --
Apr  1 11:25:19 davey-laptop -- MARK --
Apr  1 11:26:15 davey-laptop kernel: [ 2515.096326] usb 4-3: new high speed USB device using ehci_hcd and address 6
Apr  1 11:26:30 davey-laptop kernel: [ 2530.740598] usb 4-3: new high speed USB device using ehci_hcd and address 7
Apr  1 11:26:46 davey-laptop kernel: [ 2546.384863] usb 4-3: new high speed USB device using ehci_hcd and address 8
Apr  1 11:26:57 davey-laptop kernel: [ 2556.916871] usb 4-3: new high speed USB device using ehci_hcd and address 9

Any help greatly appreciated.

---

