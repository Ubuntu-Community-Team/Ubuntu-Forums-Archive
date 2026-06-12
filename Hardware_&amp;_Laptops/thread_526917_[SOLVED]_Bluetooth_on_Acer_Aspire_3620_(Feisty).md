---
title: "[SOLVED] Bluetooth on Acer Aspire 3620 (Feisty)"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by Arjunanda on 2007-08-16
I have Acer Aspire 3623WXCi running Feisty. I would like to get my bluetooth working, but I do not get it.

My Bluetooth device seems to be detected allright:
```
$ dmesg| grep -i bluet
[   33.000000] Bluetooth: Core ver 2.11
[   33.000000] Bluetooth: HCI device and connection manager initialized
[   33.000000] Bluetooth: HCI socket layer initialized
[   33.124000] Bluetooth: L2CAP ver 2.8
[   33.124000] Bluetooth: L2CAP socket layer initialized
[   33.256000] Bluetooth: RFCOMM socket layer initialized
[   33.256000] Bluetooth: RFCOMM TTY layer initialized
[   33.256000] Bluetooth: RFCOMM ver 1.8

```
But my Nokia N70 is not found.
```

$ hcitool scan
Device is not available: No such device

```
Also the blue led is not on, but as I have read, it is controlled by software and is not related to the actual bluetooth functionality itself.

How can I have my ubuntu to detect my N70 phone? How can I test my bluetooth functionality? Once this part is done, then the second part is to get the obex protocol wprking.  I have installed openobex and openobex-frontend, so that will e the next step.

I would appreciate any tips :)

Edit: I was not sure if there is bluetooth chip on this laptop or not. There is bluetooth led and button on the front panel and the dmesg listing lists bluetoot information, so I assumed there is bluetooth chip. But calling to Acer confirmed that THERE IS NO BLUETOOTH on this laptop, And how many hours did I spend in trying to fix it..

Case closed.

---

### Post by ddrichardson on 2007-08-17
Sorry to hear that, you can mark the thread as solved.

---

### Post by Arjunanda on 2007-08-17
Done. Thanks :)

---

