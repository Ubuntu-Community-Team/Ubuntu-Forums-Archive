---
title: "Belkin F8T016 Bluetooth solution"
date: 2009-04-01
forum: Hardware
---

### Post by Paul Moir on 2009-04-01
I had trouble using this mini usb dongle with kubuntu hardy.  Although the adapter was detected, communications didn't work.  That is to say, hcitool dev revealed an adapter, but communications were not successful.  hci_usb needs the parameter reset=1 for it to work.  On modern versions of ubuntu, you simply add the line:

options hci_usb reset=1 

to the file /etc/modprobe.d/options

Then pull the adapter, sudo rmmod hci_usb, and reinstall the adapter.

For people hunting for a solution:
Bus 003 Device 022: ID 050d:016a Belkin Components

Hopefully that'll help the next guy!

---

### Post by hilli2 on 2009-10-18
Works w/ Ubuntu 8.04. Thanks.

---

