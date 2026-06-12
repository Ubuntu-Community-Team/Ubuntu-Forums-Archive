---
title: "hibernate = dead webcam?"
date: 2010-06-16
forum: Hardware
---

### Post by Mauri72 on 2010-06-16
Hi all, 
I have Vaio laptop VPCEB1S0E.I was pleasantly surprised when I found out that pretty much 99% of the hardware worked well in Lucid, including the webcam (which in previous laptops I had, has always been troublesome)
HOWEVER......today I left my laptop running on battery for too long and it hibernated. Since I woke it up the webcam is not working. Cheese says there is no webcam detected and rebooting won't do anything. What did hibernate do? and is there a way to fix it?
Thanks

---

### Post by Mauri72 on 2010-06-16
dmesg output is a continuous stream of 

hub 1-1:1.0: unable to enumerate USB device on port 2
usb 1-1.2: new high speed USB device using ehci_hcd and address 84

---

### Post by the_olo on 2010-07-23
I have a Sony Vaio VPCEB1M1E and the same problem, but without hibernation - it started occuring immediately...

Here's my laptop model data from "dmidecode -t System", can you post yours?

```
# dmidecode -t System
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: Sony Corporation
        Product Name: VPCEB1M1E
        Version: C604UTDY
        Serial Number: 27524055-5002379
        UUID: A025AFC4-4BD7-DD11-8082-544249104A10
        Wake-up Type: Power Switch
        SKU Number: N/A
        Family: VAIO
```


My kernel log is flooded with these messages:


```
Jul 24 00:52:36 hostname kernel: [ 1729.480999] usb 1-1.2: new high speed USB device using ehci_hcd and address 19
Jul 24 00:52:36 hostname kernel: [ 1729.501066] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:52:37 hostname kernel: [ 1729.740753] usb 1-1.2: new high speed USB device using ehci_hcd and address 20
Jul 24 00:52:37 hostname kernel: [ 1729.762605] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:52:37 hostname kernel: [ 1730.001272] usb 1-1.2: new high speed USB device using ehci_hcd and address 21
Jul 24 00:52:37 hostname kernel: [ 1730.020871] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:52:37 hostname kernel: [ 1730.432339] usb 1-1.2: new high speed USB device using ehci_hcd and address 22
Jul 24 00:52:37 hostname kernel: [ 1730.452415] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:52:38 hostname kernel: [ 1730.930717] usb 1-1.2: new high speed USB device using ehci_hcd and address 23
Jul 24 00:52:38 hostname kernel: [ 1730.950479] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:52:38 hostname kernel: [ 1731.201876] usb 1-1.2: new high speed USB device using ehci_hcd and address 24
Jul 24 00:52:38 hostname kernel: [ 1731.222119] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:52:39 hostname kernel: [ 1731.701661] usb 1-1.2: new high speed USB device using ehci_hcd and address 25
Jul 24 00:52:39 hostname kernel: [ 1731.720890] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:52:39 hostname kernel: [ 1731.960175] usb 1-1.2: new high speed USB device using ehci_hcd and address 26
Jul 24 00:52:39 hostname kernel: [ 1731.981767] hub 1-1:1.0: unable to enumerate USB device on port 2
```

Does your kernel also report discovering the device on sequentially incrementing addresses and failing?

In my case this runs in an infinite loop and addresses wrap around at 127:

```
Jul 24 00:54:31 hostname kernel: [ 1843.533592] usb 1-1.2: new high speed USB device using ehci_hcd and address 126
Jul 24 00:54:31 hostname kernel: [ 1843.553825] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:54:31 hostname kernel: [ 1844.032766] usb 1-1.2: new high speed USB device using ehci_hcd and address 127
Jul 24 00:54:31 hostname kernel: [ 1844.053597] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:54:31 hostname kernel: [ 1844.292676] usb 1-1.2: new high speed USB device using ehci_hcd and address 3
Jul 24 00:54:31 hostname kernel: [ 1844.312818] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:54:32 hostname kernel: [ 1844.554939] usb 1-1.2: new high speed USB device using ehci_hcd and address 4
Jul 24 00:54:32 hostname kernel: [ 1844.574652] hub 1-1:1.0: unable to enumerate USB device on port 2
Jul 24 00:54:32 hostname kernel: [ 1844.812438] usb 1-1.2: new high speed USB device using ehci_hcd and address 5
Jul 24 00:54:32 hostname kernel: [ 1844.832649] hub 1-1:1.0: unable to enumerate USB device on port 2

```

---

