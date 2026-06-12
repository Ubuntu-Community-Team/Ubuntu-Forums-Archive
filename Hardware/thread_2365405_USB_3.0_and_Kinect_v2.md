---
title: "USB 3.0 and Kinect v2"
date: 2017-07-06
forum: Hardware
---

### Post by ayassin on 2017-07-06
Hello everyone,

I'm trying to run the [libfreenect2 from OpenKinect]("https://github.com/OpenKinect/libfreenect2") and when I'm trying to test it with "Protonect" the kinect is not found. My machine has both Ubuntu 14.04 and Windows 10
I get the following error:
```
$ ./bin/Protonect
Version: 0.2.0
Environment variables: LOGFILE=<protonect.log>
Usage: ./bin/Protonect [-gpu=<id>] [gl | cl | clkde | cuda | cudakde | cpu] [<device serial>]
        [-noviewer] [-norgb | -nodepth] [-help] [-version]
        [-frames <number of frames to process>]
To pause and unpause: pkill -USR1 Protonect
[Info] [Freenect2Impl] enumerating devices...
[Info] [Freenect2Impl] 6 usb devices connected
[Info] [Freenect2Impl] found 0 devices
no device connected!
```

After some reading online, I have realized the problem lies with the USB 3.0 port. The Kinect is being recognized only at USB 2.0 but not USB 3.0 even though it's connected to the USB 3.0 port.
```

$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 258a:1007  
Bus 001 Device 002: ID 045e:02d9 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/11p, 480M
**    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/1p, 480M**
    |__ Port 3: Dev 4, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 3: Dev 4, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 4: Dev 5, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 4: Dev 5, If 1, Class=Wireless, Driver=btusb, 12M
    |__ Port 5: Dev 6, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 5: Dev 6, If 1, Class=Video, Driver=uvcvideo, 480M
```

I have the access to the device under "/etc/udev/rules.d/", I have tried "lsusb -v", to boot with the kinect plugged-in, etc, and I believe my hardware is supported 
I'm really new to ubuntu and not sure how to proceed. Any help to fix this problem will be greatly appreciated!

Other info:
```

$  lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1c.5 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
09:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev a1)
0a:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter

$ dmesg | grep usb
[    0.200683] usbcore: registered new interface driver usbfs
[    0.200690] usbcore: registered new interface driver hub
[    0.200707] usbcore: registered new device driver usb
[    0.626370] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.626371] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.626373] usb usb1: Product: xHCI Host Controller
[    0.626374] usb usb1: Manufacturer: Linux 4.2.0-42-generic xhci-hcd
[    0.626376] usb usb1: SerialNumber: 0000:00:14.0
[    0.627625] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.627627] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.627628] usb usb2: Product: xHCI Host Controller
[    0.627629] usb usb2: Manufacturer: Linux 4.2.0-42-generic xhci-hcd
[    0.627631] usb usb2: SerialNumber: 0000:00:14.0
[    0.938167] usb 1-1: new high-speed USB device number 2 using xhci_hcd
[    1.068722] usb 1-1: New USB device found, idVendor=045e, idProduct=02d9
[    1.068725] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.068727] usb 1-1: Product: NuiSensor Adaptor      
[    1.068728] usb 1-1: Manufacturer: Microsoft Corporation  
[    1.242480] usb 1-3: new full-speed USB device number 3 using xhci_hcd
[    6.375612] usb 1-3: unable to read config index 0 descriptor/start: -110
[    6.375616] usb 1-3: can't read configurations, error -110
[    6.487720] usb 1-3: new full-speed USB device number 4 using xhci_hcd
[    6.618381] usb 1-3: New USB device found, idVendor=258a, idProduct=1007
[    6.618385] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.618386] usb 1-3: Product: Game Mouse
[    6.618388] usb 1-3: Manufacturer: SINOWEALTH
[    6.784019] usb 1-4: new full-speed USB device number 5 using xhci_hcd
[    6.913329] usb 1-4: New USB device found, idVendor=0bda, idProduct=b001
[    6.913332] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    6.913334] usb 1-4: Product: Bluetooth Radio 
[    6.913335] usb 1-4: Manufacturer: Realtek 
[    6.913336] usb 1-4: SerialNumber: 00e04c000001
[    7.080314] usb 1-5: new high-speed USB device number 6 using xhci_hcd
[    7.279649] usb 1-5: New USB device found, idVendor=0bda, idProduct=5776
[    7.279653] usb 1-5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    7.279654] usb 1-5: Product: HP Truevision HD
[    7.279656] usb 1-5: Manufacturer: DDTPN02BI7L7G5
[    7.279657] usb 1-5: SerialNumber: 200901010001
[   11.858474] usbcore: registered new interface driver btusb
[   12.322734] input: HP Truevision HD as /devices/pci0000:00/0000:00:14.0/us

$ lsb_release -a 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

$ uname -a
Linux cyberamajd-HP-15-Notebook-PC 4.2.0-42-generic #49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

