---
title: "Card reader does not work"
date: 2008-05-10
forum: Hardware
---

### Post by Keithamus on 2008-05-10
I have a problem with my card reader, it does not automount, and I can't see why. Here is the output of dmesg | grep usb:

```

[ 4052.477586] usb 7-1: new high speed USB device using ehci_hcd and address 8
[ 4052.542797] usb 7-1: configuration #1 chosen from 1 choice
[ 4052.544862] usb-storage: device found at 8
[ 4052.544868] usb-storage: waiting for device to settle before scanning
[ 4056.523033] usb-storage: device scan complete
[ 4073.337863] usb 7-1: reset high speed USB device using ehci_hcd and address 8

```

This seems fine to me, but it still does not work. Any ideas?

---

### Post by Keithamus on 2008-05-10
Ok, it seems to actually be a problem with a 4gb transflash card.

Looking in the forums doesn't yield much help - anyone got transflash working?

---

