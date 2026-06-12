---
title: "Teac AI-101 no audio/connection"
date: 2016-07-13
forum: Hardware
---

### Post by msknight on 2016-07-13
TEAC AI-101 Dac/Amp connecting to Linux Mint 17.3 Rosa \n \l - 64 bit
VERSION="14.04.4 LTS, Trusty Tahr"

3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

On connecting the Teac to USB 2, the device turns up in the sound control window properly, and I can select it, but when I try to send audio to it, nothing comes out and the applications stall. They don't report anything, they just hang until I select a different sound output and then they continue as if nothing happened... but on selecting the Teac, nothing wants to move.

On connecting the Teac to USB 3, it seems to connect and disconnect. Doesn't even flicker a presence in the sound window.

I did try to connect via Bluetooth as well, but it wouldn't connect for some reason. Sees it, pairs with it, trusts it, but doesn't want to use it as a device. I have an optical cable on order, but I can't see whether that will make any difference.

USB2....
[612629.199542] usb 5-2.4.2: new high-speed USB device number 18 using ehci-pci
[612629.915629] usb 5-2.4.2: new high-speed USB device number 19 using ehci-pci
[612630.009199] usb 5-2.4.2: New USB device found, idVendor=0644, idProduct=8051
[612630.009208] usb 5-2.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[612630.009213] usb 5-2.4.2: Product: TEAC AI-101 Audio
[612630.009217] usb 5-2.4.2: Manufacturer: TEAC
[612630.009221] usb 5-2.4.2: SerialNumber: ACEGIKMOQS....

USB3....
[613059.985196] usb 1-1: new high-speed USB device number 12 using xhci_hcd
[613060.118318] usb 1-1: New USB device found, idVendor=0644, idProduct=8051
[613060.118325] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[613060.118329] usb 1-1: Product: TEAC AI-101 Audio
[613060.118332] usb 1-1: Manufacturer: TEAC
[613060.118335] usb 1-1: SerialNumber: ACEGIKMOQS....
[613102.527644] usb 1-1: USB disconnect, device number 12

---

