---
title: "Samsung  YP-U2 mp3 player stopped being visible in 18.04"
date: 2020-04-12
forum: Hardware
---

### Post by shantiq on 2020-04-12
Usta work fine now it is not seen in Disks AT ALL

when i run ```
dmesg | tail

```
i get


```
dmesg | tail[43302.265140] audit: type=1400 audit(1586714016.906:56): apparmor="DENIED" operation="mknod" profile="/usr/bin/evince-thumbnailer" name="/home/shan/.thumbnails/normal/adbde95711d45bb9036677d47aa258a5.png" pid=10032 comm="evince-thumbnai" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[43382.181401] usb 1-8.4: USB disconnect, device number 21
[44328.079529] usb 1-8.4: new high-speed USB device number 22 using xhci_hcd
[44328.192399] usb 1-8.4: New USB device found, idVendor=04e8, idProduct=5050
[44328.192403] usb 1-8.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[44328.192406] usb 1-8.4: Product: YP-U2          
[44328.192409] usb 1-8.4: Manufacturer: Samsung 
[44328.192412] usb 1-8.4: SerialNumber: 4002FA761B420111
[44328.193572] usb-storage 1-8.4:1.0: USB Mass Storage device detected
[44328.194181] scsi host5: usb-storage 1-8.4:1.0



```

also


```
lsusb
Bus 002 Device 002: ID 2109:0813 VIA Labs, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bda:0153 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 022: ID 04e8:5050 Samsung Electronics Co., Ltd YP-U2 MP3 Player
Bus 001 Device 008: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 006: ID 2109:2813 VIA Labs, Inc. 
Bus 001 Device 011: ID 1210:000a DigiTech 
Bus 001 Device 005: ID 1a2c:4324 China Resource Semico Co., Ltd 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 009: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 09da:024f A4Tech Co., Ltd. RF Receiver and G6-20D Wireless Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


and gparted does NOT see it



what is the procedure to get it back in business?

Thanx in advance

[IMG]https://uk.static.webuy.com/product_images/Electronics/Media%20Players/SMP4SAM23_l.jpg[/IMG]

---

### Post by CelticWarrior on 2020-04-12
The flash memory could be dead now. 
Have you tried it in another computer?

---

### Post by shantiq on 2020-04-12
Ha   ignore previous post and will mark as solved

Problem arose i now think from having loaded and erased too many trax over time

Had to:

```
sudo mkdir /media/usb
sudo mount /dev/sdc1 /media/usb
```
to see it again THEN >>

Solution simply was to ***reformat with Disks to FAT16 not FAT32*** as this makes player unusable; if anyone has done that already no biggie it can be reformatted


I leave this here as might be of use to other visitors to site

---

