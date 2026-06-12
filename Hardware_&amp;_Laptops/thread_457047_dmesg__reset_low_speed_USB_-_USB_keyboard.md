---
title: "dmesg:  reset low speed USB - USB keyboard"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by apjone on 2007-05-28
My dmesg and /var/log/messages is of

May 28 16:00:43 kyo kernel: [17180579.308000] usb 1-2: reset low speed USB device using ohci_hcd and address 3
May 28 16:00:48 kyo kernel: [17180584.624000] usb 1-2: reset low speed USB device using ohci_hcd and address 3
May 28 16:00:53 kyo kernel: [17180589.304000] usb 1-2: reset low speed USB device using ohci_hcd and address 3

It seems when thiiiiiiiiis happens every few seconds it repeats thhhhhhhhhe last key pressed. I am typing thissssssss with the keyboarrrrrrrrrd just as an example oooooooof how bad it is.

Any ideas on how to fix this?

I ammmmmmm running ubunut 6.10 .

root@kyo:~# lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0a81:0101 Chesen Electronics Corp. Keyboard

---

### Post by apjone on 2007-05-28
Appears it was my mouse, unplugged all usb device's and plugged back in and now is working. 

very odd.

---

