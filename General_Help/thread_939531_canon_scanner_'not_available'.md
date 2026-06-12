---
title: "canon scanner 'not available'"
date: 2008-10-06
forum: General Help
---

### Post by orengolan on 2008-10-06
I bought [Canon Canoscan lide 200]("http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&fcategoryid=119&modelid=17103#DownloadDetailAct") (usb scanner).
I connect to my laptop but It's not scanning when I hit the scan button.
application->graphics->Xsane inage scanner shows 'no device available'.

I did the following:
```
sudo apt-get install libsane-extras
sudo apt-get install sane-utils
sudo adduser $USER scanner
```

I log-out and log-in again and run the following:
scanimage -L
sudo sane-find-scanner
sane-find-scanner

**here are the results:**

scanimage -L
```
No scanners were identified.
``` 

sane-find-scanner
```
found USB scanner (vendor=0x04a9, product=0x1905, chip=GL843?) at libusb:005:014
found USB scanner (vendor=0x0483, product=0x2016) at libusb:003:003

```
lsusb
```
Bus 005 Device 014: ID 04a9:1905 Canon, Inc.
```
lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:08.0 Ethernet controller: Intel Corporation PRO/100 VM Network Connection (rev 02)
```
dmesg | tail -n 40
```
[12924.431454] usb 2-1: new full speed USB device using uhci_hcd and address 4
[12924.586524] usb 2-1: configuration #1 chosen from 1 choice
[12924.590143] ch341 2-1:1.0: pl2303 converter detected
[12924.590357] usb 2-1: pl2303 converter now attached to ttyUSB0
[13601.710215] usb 2-1: USB disconnect, address 4
[13601.710838] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[13601.710867] ch341 2-1:1.0: device disconnected
[13610.523319] usb 2-1: new full speed USB device using uhci_hcd and address 5
[13610.677213] usb 2-1: configuration #1 chosen from 1 choice
[13610.682938] ch341 2-1:1.0: pl2303 converter detected
[13610.683159] usb 2-1: pl2303 converter now attached to ttyUSB0
[13636.637480] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[13636.639485] ch341 2-1:1.0: device disconnected
[16945.015724] usb 5-1: USB disconnect, address 2
[16946.488467] usb 2-1: USB disconnect, address 5
[17643.482368] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[17643.773975] usb 3-1: reset full speed USB device using uhci_hcd and address 3
[24662.711506] usb 5-3: new high speed USB device using ehci_hcd and address 8
[24662.844977] usb 5-3: configuration #1 chosen from 1 choice
[24902.559204] usb 5-3: USB disconnect, address 8
[25094.403635] usb 5-3: new high speed USB device using ehci_hcd and address 9
[25094.537126] usb 5-3: configuration #1 chosen from 1 choice
[25168.358710] usb 5-3: USB disconnect, address 9
[25176.604087] usb 5-1: new high speed USB device using ehci_hcd and address 10
[25176.737627] usb 5-1: configuration #1 chosen from 1 choice
[25457.084713] usb 5-1: USB disconnect, address 10
[25564.667195] usb 5-3: new high speed USB device using ehci_hcd and address 11
[25564.800848] usb 5-3: configuration #1 chosen from 1 choice
[30640.846428] usb 5-3: USB disconnect, address 11
[30657.663028] usb 5-3: new high speed USB device using ehci_hcd and address 12
[30657.796563] usb 5-3: configuration #1 chosen from 1 choice
[30771.849270] usb 5-3: USB disconnect, address 12
[30777.815710] usb 5-1: new high speed USB device using ehci_hcd and address 13
[30777.949213] usb 5-1: configuration #1 chosen from 1 choice
[32793.072402] usb 5-1: USB disconnect, address 13
[32794.974492] usb 5-3: new high speed USB device using ehci_hcd and address 14
[32795.107962] usb 5-3: configuration #1 chosen from 1 choice
[34542.561308] UDF-fs: No VRS found
[34542.602647] ISO 9660 Extensions: Microsoft Joliet Level 1
[34542.648900] ISOFS: changing to secondary root
```

---

