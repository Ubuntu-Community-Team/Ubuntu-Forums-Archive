---
title: "Problema con un dischi da 1TB usb 3.0"
date: 2024-10-20
forum: Hardware
---

### Post by Dr Berta on 2024-10-20
Ciao,
ho comprato due dischi usb 3.0 esterni da 1TB formattati NTFS: uno della Western Digital e un altro cinese.
A volte il disco WD non viene visto e dando il comando dmesg si ottiene questa risposta:
xhci_hcd 0000:03:00.0: xHCI host controller not responding, assume dead
```
[ 1879.251727] xhci_hcd 0000:03:00.0: xHCI host controller not responding, assume dead
[ 1879.251727] xhci_hcd 0000:03:00.0: HC died; cleaning up
```

Mentre il disco cinese proprio non viene visto se collegato ad una porta USB 3.0. Collegandolo ad una porta USB 2.0 dmesg fornisce questo feedback:
```
[ 9416.357979] usb 3-1: new high-speed USB device number 8 using ehci-pci[ 9416.563270] usb 3-1: New USB device found, idVendor=152d, idProduct=0578, bcdDevice= 2.09
[ 9416.563279] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9416.563283] usb 3-1: Product: USB to ATA/ATAPI Bridge
[ 9416.563287] usb 3-1: Manufacturer: JMicron
[ 9416.563290] usb 3-1: SerialNumber: 0123456789ABCDEF
``` ma poi nessun tool riesce a vedere il disco.

Entrambi i dischi funzionano bene su Windows.

Il mio sistema ha ubuntu 20.04 su una scheda madre ASUS M4A87TD-USB3 con processore phenom II 965 quad core e 16GB di RAM (lo sò, è un pò datato...)
I fabbricanti dicono che i dischi sono compatibili con Linux. Su un sistema con Ubuntu 24.04 i dischi vengono visti.

Suggerimenti?

Grazie
Claudio

---

### Post by yancek on 2024-10-20
What is the purpose of the disk if it is formatted with the windows ntfs filesystem?  Are you planning to use it to share data between windows and Ubuntu?  Have you had this disk attached to a windows OS?  If so, which?  Of course one would expect a proprietary windows filesystem to work better on a windows OS.

---

### Post by Dr Berta on 2024-10-20
The purpose is to use them as portable data disks. In particular I would use them with virtual machines. 
In particular my main pc has linux as operative system, but my laptop has Windows 11

---

### Post by yancek on 2024-10-21
If you have the device attached to windows, you need to safely remove the device in windows before shutting down windows or Linux won't access it.  The information in your original post shows the device is detected.  Do you get any messages when you try to mount the drive/partition in Linux?  Have you tried manually mounting it?

---

