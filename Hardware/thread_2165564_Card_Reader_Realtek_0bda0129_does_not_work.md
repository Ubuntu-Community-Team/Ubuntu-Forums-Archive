---
title: "Card Reader Realtek 0bda:0129 does not work"
date: 2013-08-05
forum: Hardware
---

### Post by Ole_M on 2013-08-05
Hi everyone,

on my Laptop (Samsung Chronos Series 7: 770z5e) the Card Reader does not work. In Windows 8 it works fine. Under Ubuntu 13.04 when inserting a card nothing happens, except [FONT=courier new]xhci_queue_intr_tx: 72 callbacks suppressed[/FONT] keep piling up in [FONT=courier new]dmesg[/FONT].
```

> dmesg | tail
[10153.717249] xhci_queue_intr_tx: 70 callbacks suppressed
[10158.829518] xhci_queue_intr_tx: 70 callbacks suppressed
[10163.941762] xhci_queue_intr_tx: 70 callbacks suppressed
[10169.054011] xhci_queue_intr_tx: 70 callbacks suppressed
[10174.166195] xhci_queue_intr_tx: 70 callbacks suppressed
[10179.278454] xhci_queue_intr_tx: 70 callbacks suppressed
[10184.390735] xhci_queue_intr_tx: 70 callbacks suppressed
[10189.502970] xhci_queue_intr_tx: 70 callbacks suppressed
[10194.615192] xhci_queue_intr_tx: 70 callbacks suppressed
[10199.727466] xhci_queue_intr_tx: 70 callbacks suppressed
```


It's a Realtek Card Reader with the ID [0bda:0129].
```
> lsusb 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 1b1c:1b05 Corsair 
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 2232:1045  
Bus 002 Device 003: ID 8087:07da Intel Corp. 
```

The driver rts5139 is loaded.
```
> lsmod | grep rts5139
rts5139               352481  0 
```

---

### Post by fabio3 on 2014-01-11
Try this:
[http://permalink.gmane.org/gmane.linux.kernel/1500485](http://permalink.gmane.org/gmane.linux.kernel/1500485)

It did not work for me, though. Only the "xhci_queue_intr_tx: XX callbacks suppressed" messages stopped, but the card is not being read yet.

But it worked for a lot of people out there, so it's worth trying.


Fabio

---

### Post by erwin6 on 2014-02-20
I have exactly the same laptop as you and I think there may be still some timing issues.

But I have found a workaround which may help in other similar situations as well
If the SD card is in the reader while loading the rts5139 module it is recognized and can be mounted.
So the procedure shoud be as follows:

- Remove module:
```
sudo rmmod rts5139
```
- Insert SD card
- Load module:
```
sudo modprobe rts5139
```
Now the SD card should be available

---

### Post by erwin6 on 2014-02-20
A little digging into the problem with the kernel module DEBUG enabled showed that an /dev/sdb1 device should be created at insertion of a xD/SD-card. But this obviously only happens only if the card is already there at module loading.

But I found another way (than the one in my previous post using sudo) by "waking" the sdb-device with pmount.
Invoke it with
```
pmount sdb
```

shortly after that the wanted sdb1-device appears and should be recognized by the available desktop environment!!

---

