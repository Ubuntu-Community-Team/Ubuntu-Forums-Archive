---
title: "D865GLC, USB2 issues with iPhone 3G"
date: 2009-07-13
forum: Hardware
---

### Post by edy80y on 2009-07-13
Hi,

I am using an intel D865GLC mb running Jaunty and when i plug in my iPhone, 'sudo tail -f /var/log/messages' spits out the following message:

Jun 23 07:56:10 edy80y-ubuntu kernel: [ 469.160104] usb 1-8: USB disconnect, address 6
Jun 23 07:56:18 edy80y-ubuntu kernel: [ 477.620019] usb 1-8: new high speed USB device using ehci_hcd and address 7
Jun 23 07:56:18 edy80y-ubuntu kernel: [ 477.944017] usb 5-2: new full speed USB device using uhci_hcd and address 3
Jun 23 07:56:19 edy80y-ubuntu kernel: [ 478.090015] usb 5-2: not running at top speed; connect to a high speed hub
Jun 23 07:56:19 edy80y-ubuntu kernel: [ 478.161457] usb 5-2: configuration #1 chosen from 4 choices
Jun 23 07:56:19 edy80y-ubuntu kernel: [ 478.246053] ttyS1: LSR safety check engaged!
Jun 23 07:56:19 edy80y-ubuntu kernel: [ 478.361615] ttyS1: LSR safety check engaged!

i tested it on all usb ports, and on a couple of them the iphone started to act retarded, like i was plugging and unplugging the usb cable.

But, when i load VirtualBox, the guest OS (XP Pro) detects the device as being connected to a low speed port as well.

When i plug in my Canon iXus or iPod nano, both are recognized as high-speed devices in Ubuntu when i 'sudo tail -f /var/log/messages', and also in the VBox Guess OS.

Cheers,
Eddie

---

