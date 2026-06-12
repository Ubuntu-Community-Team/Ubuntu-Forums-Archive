---
title: "USB hard drive &amp; USB headset do not work together Ubuntu 7.10"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Stetzen on 2007-10-31
I have Ubuntu 7.10 installed on my laptop Toshiba Satellite A75 with ATI motherboard. There are Seagate USB hard drive and Logitech USB headset plugged to it. Apart from each other these devices work OK, but if I'm trying to use them together (watching film from the hard drive of listening to music while something is copying from the hard drive) all my USB system simply turns off after a while (from few seconds up to one hour). dmesg command does not mention anything unusual just after USB failure, but if I'm trying to reconnect any of my USB devices, it write
 ```
[  270.584398] usb 1-2: USB disconnect, address 3
[  274.571085] ohci_hcd 0000:00:13.0: IRQ INTR_SF lossage
[  274.571097] ohci_hcd 0000:00:13.0: leak ed dfcc8080 (#81) state 0 (has tds)
```

It looks like the living time depends from the intensity of data transfer from the hard disc (the shortest time is when I'm trying to navigate through the film).

My BIOS is fully upgraded, boot options like noapic, irqpoll, pci=noacpi don't solve the problem. 

My logs are attached.

If anybody knows, please help!!

---

