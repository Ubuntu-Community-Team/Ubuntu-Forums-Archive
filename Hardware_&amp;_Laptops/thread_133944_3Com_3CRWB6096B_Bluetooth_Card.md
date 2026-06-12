---
title: "3Com 3CRWB6096B Bluetooth Card"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by shilliard on 2006-02-21
Hi

Recently got a 3com PCMCIA bluetooth card (3CRWB6096B) with the understanding that it was supported by linux.

When I plug into my laptop (Acer Aspire 5024) it freezes up. If I unplug all is well again, dmesg showed this:

serial8250: too much work for irq20
serial8250: too much work for irq20
...
...

I running 5.10 and have all the latest kernel updates. Have scrolled the forums looking for a solution and found little, the drivers all appear to be there.

Thanks

---

### Post by shilliard on 2006-06-30
Just to follow up - it works fine in Dapper.

When the card is inserted an entry appears in System->Administration->Device Manager.  Examining this entry shows that it was using the /dev/ttyS4 UART

Then run the command:

$ hciattach /dev/ttyS4 3com

This attaches the device to the Bluez stack.  It should now be possible to detect bluetooth devices using:

$ sudo hcitool scan

Following this [wiki]("https://help.ubuntu.com/community/BluetoothDialup") guide allowed me to set up a GPRS connection using a Nokia 6230.

Top quality.

---

