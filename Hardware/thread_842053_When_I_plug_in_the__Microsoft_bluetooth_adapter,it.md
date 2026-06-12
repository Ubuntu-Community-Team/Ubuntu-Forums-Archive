---
title: "When I plug in the  Microsoft bluetooth adapter,it can not be recognized!"
date: 2008-06-27
forum: Hardware
---

### Post by moreal008 on 2008-06-27
I am using ubuntu 8.04,the newest blue-utils and gnome bluth has been installed.
 Microsoft&#65533; Wireless Notebook Presenter Mouse 8000 adapter can not be recognized ,how to let the bluetooth mouse work fine,thank you in advance.
my laptop is thinkpad T41 2373 7KC
when I use lsusb, display

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0713 Microsoft Corp. 
Bus 002 Device 002: ID 045e:0707 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

use command line

cat /proc/bus/input/devices

 display:



I: Bus=0003 Vendor=045e Product=0713 Version=0111
N: Name="Microsoft Microsoft&#65533; Wireless Notebook Presenter Mouse 8000"
P: Phys=usb-0000:00:1d.1-2.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input11
U: Uniq=00125A5F6185
H: Handlers=kbd mouse3 event11 
B: EV=1f
B: KEY=37fff ac3027 bf004444 0 0 1f0001 f84 8a37c400 667bfa d9715fed 8e0000 0 0 0
B: REL=3c3
B: ABS=1 0
B: MSC=10

moreal@moreal-T41:~$ dmesg | grep usb
[    7.922232] usbcore: registered new interface driver usbfs
[    7.922263] usbcore: registered new interface driver hub
[    7.930211] usbcore: registered new device driver usb
[    7.945042] usb usb1: configuration #1 chosen from 1 choice
[    8.046967] usb usb2: configuration #1 chosen from 1 choice
[    8.150977] usb usb3: configuration #1 chosen from 1 choice
[    8.274274] usb usb4: configuration #1 chosen from 1 choice
[  105.950555] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  106.142719] usb 2-2: configuration #1 chosen from 1 choice
[  106.471615] usb 2-2.3: new full speed USB device using uhci_hcd and address 3
[  106.634740] usb 2-2.3: configuration #1 chosen from 1 choice
[  106.949491] usbcore: registered new interface driver hiddev
[  106.962778] input: Microsoft Microsoft&#65533; Wireless Notebook Presenter Mouse 8000 as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input11
[  107.002488] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft&#65533; Wireless Notebook Presenter Mouse 8000] on usb-0000:00:1d.1-2.3
[  107.002515] usbcore: registered new interface driver usbhid
[  107.002520] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

---

