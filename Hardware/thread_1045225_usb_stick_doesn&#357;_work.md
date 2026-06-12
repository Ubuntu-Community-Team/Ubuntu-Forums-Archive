---
title: "usb stick doesn&#357; work"
date: 2009-01-20
forum: Hardware
---

### Post by dockalek on 2009-01-20
My computer doesn&#357; recognize any flashdiscs anymore, whatsmore, it seems to destroy it..doesn't work afterward on any other computer and system at all. (three destroyed devices so far)
This is just the very end of a reply:

[ 6231.464370] usb 3-2: device descriptor read/64, error -71
[ 6231.688049] usb 3-2: device descriptor read/64, error -71
[ 6231.904048] usb 3-2: new low speed USB device using uhci_hcd and address 59
[ 6232.024054] usb 3-2: device descriptor read/64, error -71
[ 6232.248050] usb 3-2: device descriptor read/64, error -71
[ 6232.464046] usb 3-2: new low speed USB device using uhci_hcd and address 60
[ 6232.876025] usb 3-2: device not accepting address 60, error -71
[ 6232.988044] usb 3-2: new low speed USB device using uhci_hcd and address 61
[ 6233.396032] usb 3-2: device not accepting address 61, error -71
[ 6233.397603] hub 3-0:1.0: unable to enumerate USB device on port 2

Thanx for help

---

### Post by dabl on 2009-01-20
Try running a Live CD on that computer, then stick a USB stick into the connector and see if it is recognized.  If not, it's a hardware problem with your computer.  If you can make and use a Live CD of another distro (sidux, elive, whatever) that would prove it is unrelated to *buntu.

I doubt your prior devices are destroyed -- probably you can "dd" them back to life, if they can be recognized on the bus with a /dev/sdx number.  You'll have to zeroize the MBR:

> dd if=/dev/zero of=/dev/sd*x* bs=512 count=1

Don't make a mistake on the *x* -- this command will also zeroize your hard drive if you get the "x" wrong, so be sure before you issue the command.

Then you'll have to use GParted, Qparted, or some other partitioning utility to create a partition table, and then you can format it.

---

