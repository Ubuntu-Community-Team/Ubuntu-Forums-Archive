---
title: "Printer stopped working...didn't change anything"
date: 2008-10-12
forum: General Help
---

### Post by jorwex on 2008-10-12
Hey all,

My printer stopped working. Ubuntu keeps asking if it got disconnected. It's a Lexmark laser printer connected via USB. I dual boot with Windows and it still talks to it fine. 
What can I check?

Edit: Here's some useful info. SOrry for not attaching it before

```
~$-f /var/log/messages
Oct 12 22:33:34 jordan-pc dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 12 22:33:34 jordan-pc dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 12 22:33:34 jordan-pc dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Oct 12 22:33:35 jordan-pc kernel: [   53.233567] NET: Registered protocol family 10
Oct 12 22:33:35 jordan-pc kernel: [   53.233761] lo: Disabled Privacy Extensions
Oct 12 22:33:35 jordan-pc kernel: [   53.234066] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 12 22:33:35 jordan-pc pulseaudio[6874]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Oct 12 22:33:35 jordan-pc pulseaudio[6874]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct 12 22:52:26 jordan-pc kernel: [ 1185.822311] usb 3-1: USB disconnect, address 2
Oct 12 22:52:26 jordan-pc kernel: [ 1185.822510] usblp0: removed
Oct 12 22:53:00 jordan-pc kernel: [ 1219.024669] usb 3-2: new full speed USB device using uhci_hcd and address 3
Oct 12 22:53:00 jordan-pc kernel: [ 1219.210701] usb 3-2: configuration #1 chosen from 1 choice
Oct 12 22:53:00 jordan-pc kernel: [ 1219.217636] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x043D pid 0x00D7

```

```
~$ lpinfo -v
network socket
network beh
direct hpfax
direct hp
network http
network ipp
direct hal:///org/freedesktop/Hal/devices/usb_device_43d_d7_72C50TK_if0_printer_noserial
network lpd
file cups-pdf:/
direct scsi

```

---

