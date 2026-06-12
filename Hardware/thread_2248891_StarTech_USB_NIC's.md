---
title: "StarTech USB NIC's"
date: 2014-10-17
forum: Hardware
---

### Post by scojopa on 2014-10-17
Any insight on why these two NICS are not showing up? Is there something else I have to do? I installed the drivers and insmod'd them to the kernel. running 14.04 Any help would be appreciated - Thanks

```
[ 2177.936907] usb 2-1.2: USB disconnect, device number 4[ 2177.936915] usb 2-1.2.1: USB disconnect, device number 8
[ 2177.937019] ax88179_178a 2-1.2.1:1.0 eth2: unregister 'ax88179_178a' usb-0000:00:1d.0-1.2.1, ASIX AX88179 USB 3.0 Gigabit Ethernet
[ 2177.955746] ax88179_178a 2-1.2.1:1.0 (unregistered net_device): Failed to write reg index 0x0002: -19
[ 2177.955753] ax88179_178a 2-1.2.1:1.0 (unregistered net_device): Failed to write reg index 0x0001: -19
[ 2177.955758] ax88179_178a 2-1.2.1:1.0 (unregistered net_device): Failed to write reg index 0x0002: -19
[ 2179.217904] usb 2-1.1: USB disconnect, device number 3
[ 2179.217910] usb 2-1.1.1: USB disconnect, device number 7
[ 2179.217993] ax88179_178a 2-1.1.1:1.0 eth3: unregister 'ax88179_178a' usb-0000:00:1d.0-1.1.1, ASIX AX88179 USB 3.0 Gigabit Ethernet
[ 2179.244607] ax88179_178a 2-1.1.1:1.0 (unregistered net_device): Failed to write reg index 0x0002: -19
[ 2179.244615] ax88179_178a 2-1.1.1:1.0 (unregistered net_device): Failed to write reg index 0x0001: -19
[ 2179.244620] ax88179_178a 2-1.1.1:1.0 (unregistered net_device): Failed to write reg index 0x0002: -19
[ 2205.104790] usb 2-1.1: new high-speed USB device number 9 using ehci-pci
[ 2205.200747] usb 2-1.1: New USB device found, idVendor=2109, idProduct=2811
[ 2205.200754] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2205.200757] usb 2-1.1: Product: USB2.0 Hub             
[ 2205.200760] usb 2-1.1: Manufacturer: VIA Labs, Inc.         
[ 2205.201269] hub 2-1.1:1.0: USB hub found
[ 2205.201720] hub 2-1.1:1.0: 4 ports detected
[ 2207.654763] usb 2-1.1.1: new high-speed USB device number 11 using ehci-pci
[ 2207.765490] usb 2-1.1.1: New USB device found, idVendor=0b95, idProduct=1790
[ 2207.765497] usb 2-1.1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2207.765500] usb 2-1.1.1: Product: AX88179
[ 2207.765503] usb 2-1.1.1: Manufacturer: ASIX Elec. Corp.
[ 2207.765506] usb 2-1.1.1: SerialNumber: 00000000000001
[ 2208.089236] ASIX USB Ethernet Adapter:v1.10.0 21:07:18 Oct 17 2014
[ 2208.089236]         http://www.asix.com.tw
[ 2208.089247] ax88179_178a 2-1.1.1:1.0 (unregistered net_device): mtu 1500
[ 2208.089562] ax88179_178a 2-1.1.1:1.0 eth2: register 'ax88179_178a' at usb-0000:00:1d.0-1.1.1, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:0a:cd:26:77:02
[ 2210.480972] usb 2-1.2: new high-speed USB device number 12 using ehci-pci
[ 2210.576181] usb 2-1.2: New USB device found, idVendor=2109, idProduct=2811
[ 2210.576187] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2210.576191] usb 2-1.2: Product: USB2.0 Hub             
[ 2210.576194] usb 2-1.2: Manufacturer: VIA Labs, Inc.         
[ 2210.576704] hub 2-1.2:1.0: USB hub found
[ 2210.577172] hub 2-1.2:1.0: 4 ports detected
[ 2213.047137] usb 2-1.2.1: new high-speed USB device number 14 using ehci-pci
[ 2213.157583] usb 2-1.2.1: New USB device found, idVendor=0b95, idProduct=1790
[ 2213.157589] usb 2-1.2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2213.157593] usb 2-1.2.1: Product: AX88179
[ 2213.157596] usb 2-1.2.1: Manufacturer: ASIX Elec. Corp.
[ 2213.157599] usb 2-1.2.1: SerialNumber: 00000000000001
[ 2213.481404] ASIX USB Ethernet Adapter:v1.10.0 21:07:18 Oct 17 2014
[ 2213.481404]         http://www.asix.com.tw
[ 2213.481414] ax88179_178a 2-1.2.1:1.0 (unregistered net_device): mtu 1500
[ 2213.481711] ax88179_178a 2-1.2.1:1.0 eth3: register 'ax88179_178a' at usb-0000:00:1d.0-1.2.1, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:0a:cd:26:79:39



```

---

