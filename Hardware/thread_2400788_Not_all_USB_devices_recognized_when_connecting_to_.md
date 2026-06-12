---
title: "Not all USB devices recognized when connecting to a large USB Hub"
date: 2018-09-10
forum: Hardware
---

### Post by maxgerhardt on 2018-09-10
For development, I bought a USB hub with 28 USB hubs: [Manhattan MondoHub II]("http://www.manhattan-products.com/mondohub-ii"). The device is powered by an external power supply, sufficient for my use case.

On the USB hub, 15 development boards are connected (STMicro Nucleo boards). Basically, once you plug the dev board in a USB port, the ST-Link v2 chip exposes the underlying microcontroller's flash as a USB drive, on which you can drag-and-drop a firmware file. The board is then flashed with that firmware. I need to flash them automatically. Thus, I connect every board to the hub and run a script which flashes everything.

The problem is that not all of the 15 connected devices are recognized. Only 11 of them are. `dmesg` throws errors about the USB host controller not having enough resources. 

Internally, the USB hub seems to be composed of multiple USB hubs.

dmesg when I plug in the USB hub, no devices connected:

```

[269831.218406] usb 2-3: new high-speed USB device number 91 using xhci_hcd
[269831.369806] usb 2-3: New USB device found, idVendor=2109, idProduct=2811
[269831.369813] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[269831.369817] usb 2-3: Product: USB2.0 Hub            
[269831.369821] usb 2-3: Manufacturer: VIA Labs, Inc.        
[269831.370918] hub 2-3:1.0: USB hub found
[269831.371195] hub 2-3:1.0: 4 ports detected
[269831.678404] usb 2-3.1: new high-speed USB device number 92 using xhci_hcd
[269831.790645] usb 2-3.1: New USB device found, idVendor=1a40, idProduct=0201
[269831.790650] usb 2-3.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[269831.790654] usb 2-3.1: Product: USB 2.0 Hub [MTT]
[269831.791150] hub 2-3.1:1.0: USB hub found
[269831.791177] hub 2-3.1:1.0: 7 ports detected
[269831.886375] usb 2-3.2: new high-speed USB device number 93 using xhci_hcd
[269831.998500] usb 2-3.2: New USB device found, idVendor=1a40, idProduct=0201
[269831.998504] usb 2-3.2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[269831.998506] usb 2-3.2: Product: USB 2.0 Hub [MTT]
[269831.998942] hub 2-3.2:1.0: USB hub found
[269831.998964] hub 2-3.2:1.0: 7 ports detected
[269832.090378] usb 2-3.3: new high-speed USB device number 94 using xhci_hcd
[269832.202654] usb 2-3.3: New USB device found, idVendor=1a40, idProduct=0201
[269832.202658] usb 2-3.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[269832.202660] usb 2-3.3: Product: USB 2.0 Hub [MTT]
[269832.203232] hub 2-3.3:1.0: USB hub found
[269832.203258] hub 2-3.3:1.0: 7 ports detected
[269832.294400] usb 2-3.4: new high-speed USB device number 95 using xhci_hcd
[269832.415440] usb 2-3.4: New USB device found, idVendor=14cd, idProduct=8601
[269832.415449] usb 2-3.4: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[269832.415454] usb 2-3.4: Product: USB 2.0 Hub            
[269832.415458] usb 2-3.4: Manufacturer: USB Device  
[269832.416721] hub 2-3.4:1.0: USB hub found
[269832.416838] hub 2-3.4:1.0: 4 ports detected

```

When disconnecting:

```

[269873.242343] usb 2-3: USB disconnect, device number 91
[269873.242349] usb 2-3.1: USB disconnect, device number 92
[269873.243596] usb 2-3.2: USB disconnect, device number 93
[269873.244672] usb 2-3.3: USB disconnect, device number 94
[269873.245725] usb 2-3.4: USB disconnect, device number 95

```

I then connect board after board. Board 1 through 11 are recognized and cause this type of message:

```

[269950.734094] usb 2-3.2.1: new full-speed USB device number 103 using xhci_hcd
[269950.856137] usb 2-3.2.1: New USB device found, idVendor=0483, idProduct=374b
[269950.856140] usb 2-3.2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[269950.856142] usb 2-3.2.1: Product: STM32 STLink
[269950.856144] usb 2-3.2.1: Manufacturer: STMicroelectronics
[269950.856146] usb 2-3.2.1: SerialNumber: 0671FF323532543457250836
[269950.911199] usb-storage 2-3.2.1:1.1: USB Mass Storage device detected
[269950.911377] scsi host5: usb-storage 2-3.2.1:1.1
[269950.911809] cdc_acm 2-3.2.1:1.2: ttyACM2: USB ACM device
[269951.942405] scsi 5:0:0:0: Direct-Access     MBED     microcontroller  1.0  PQ: 0 ANSI: 2
[269951.942686] sd 5:0:0:0: Attached scsi generic sg4 type 0
[269951.942980] sd 5:0:0:0: [sdd] 2080 512-byte logical blocks: (1.06 MB/1.02 MiB)
[269951.943876] sd 5:0:0:0: [sdd] Write Protect is off
[269951.943887] sd 5:0:0:0: [sdd] Mode Sense: 03 00 00 00
[269951.944137] sd 5:0:0:0: [sdd] No Caching mode page found
[269951.944143] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[269951.963779] sd 5:0:0:0: [sdd] Attached SCSI removable disk 
```

When I connect the 12th board, it is not recognized. Log:

```

[270155.277574] usb 2-3.2.6: new full-speed USB device number 112 using xhci_hcd
[270155.407457] usb 2-3.2.6: New USB device found, idVendor=0483, idProduct=374b
[270155.407464] usb 2-3.2.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[270155.407468] usb 2-3.2.6: Product: STM32 STLink
[270155.407472] usb 2-3.2.6: Manufacturer: STMicroelectronics
[270155.407476] usb 2-3.2.6: SerialNumber: 066DFF323532543457074843
[270155.408451] usb 2-3.2.6: Not enough host controller resources for new device state.
[270155.408681] usb 2-3.2.6: can't set config #1, error -12

```

What's going on here? Am I being limited by the USB protocol, by hub, or by my kernel / drivers?

Running Ubuntu Budgie '18.04.1 LTS (Bionic Beaver)' on a Lenovo ThinkPad E550.

Will fetch more logs if needed. Full log file: [https://pastebin.com/BarBHwnc](https://pastebin.com/BarBHwnc)

---

### Post by Tadaen_Sylvermane on 2018-09-12
I think you can rule out usb protocol. To my knowledge you can put 256 devices on a single usb port. Terrible performance but it should work.

That hub is a beast.

---

### Post by maxgerhardt on 2018-09-13
Interesting: On a different laptop with Windows 10 installed, I got 19 devices to show up on a hub where 26 were connected. Now what would be interesting is if I put the same Ubuntu Budgie on it and see how many it recognizes. That would make a difference between the Linux and Windows drivers visible within the same chipset, if it is a USB chipset issue from my side. Seems to be quite random how many devices are recognized, depending on the machine. Will report soon.

---

### Post by maxgerhardt on 2018-09-20
It seems that this was an issue with my Laptop / its USB chipset. I switched to a Desktop PC whose motherboard has lots of USB connections. There, Windows 10 and Linux (Debian 9) both recognized every 100 device flawlessly with no "Not enough host controller resources" message popping up.

---

