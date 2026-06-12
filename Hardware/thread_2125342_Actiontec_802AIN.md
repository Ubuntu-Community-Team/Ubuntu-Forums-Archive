---
title: "Actiontec 802AIN"
date: 2013-03-13
forum: Hardware
---

### Post by Remmelas on 2013-03-13
I've an actiontec usb wifi unit..model 802AIN that I cannot for the life of me get to work. staring at dmesg, it looks like it tries...then the device doesn't communicate. relevant info below, any help with where to look for the problem would be hugely appreciated. From everything I can google up, the chipset is supported, the unit requires usb_modeswitch to be installed (it is).

dmesg:
[ 2651.071546] usb 1-1.2: >new high-speed USB device number 10 using ehci_hcd
[ 2651.107446] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 28
[ 2651.107455] evbug: Event. Dev: input2, Type: 1, Code: 28, Value: 0
[ 2651.107465] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
[ 2651.211569] usb 1-1.2: >New USB device found, idVendor=1668, idProduct=1200
[ 2651.211576] usb 1-1.2: >New USB device strings: Mfr=16, Product=32, SerialNumber=48
[ 2651.211581] usb 1-1.2: >Product: USB Device
[ 2651.211584] usb 1-1.2: >Manufacturer: ATHEROS
[ 2651.211587] usb 1-1.2: >SerialNumber: 12345
[ 2651.212248] usb 1-1.2: >ath9k_htc: Firmware htc_7010.fw requested
[ 2651.248848] usb 1-1.2: >ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
[ 2652.244570] ath9k_htc 1-1.2:1.0: >ath9k_htc: Target is unresponsive
[ 2652.244586] ath9k_htc: Failed to initialize the device
[ 2652.253629] usb 1-1.2: >ath9k_htc: USB layer deinitialized
[ 2652.924439] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 209
[ 2652.924447] evbug: Event. Dev: input2, Type: 1, Code: 109, Value: 1
[ 2652.924456] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
[ 2653.163697] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 209
[ 2653.163707] evbug: Event. Dev: input2, Type: 1, Code: 109, Value: 2
[ 2653.163718] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0
[ 2653.198608] evbug: Event. Dev: input2, Type: 4, Code: 4, Value: 209
[ 2653.198614] evbug: Event. Dev: input2, Type: 1, Code: 109, Value: 2
[ 2653.198621] evbug: Event. Dev: input2, Type: 0, Code: 0, Value: 0

---

