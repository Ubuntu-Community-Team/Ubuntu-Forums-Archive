---
title: "External USB HDD (SCSI emulation or usb error?)"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by Neg127 on 2006-02-16
I have been doing lots of things to figure out what the issue is with my system not seeing my6 external usb hard drive.  It was previously working just fine auto mounted, or manualy mounted.  I'm not exactly sure when it stoped working as I havent tried to access the drive for some time.  But here is the information on the steps I have taken to figure out what the issues could be.

From what I can see and what I have read I beleave it is an scsi emulation error or an scsi error of some sort as /dev/sd* are not in the /dev difectory.

Here is the info.



```

root@alpha:/home/mike # lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 002: ID 0402:5621 ALi Corp. USB 2.0 Storage Device
Bus 001 Device 001: ID 0000:0000
---------------------------------------------------------------------
dmesg | grep -i "SCSI device"
there are not any devices found
-----------------------------------------------------------
root@alpha:/home/mike # dmesg | grep -i "SCSI"
[4294679.870000] SCSI subsystem initialized
[4294679.876000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294684.894000]   Type:   Direct-Access                      ANSI SCSI revision: 00
-----------------------------------------------------------------------
root@alpha:/dev # cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: USB 2.0  Model: Storage Device   Rev: 0100
  Type:   Direct-Access                    ANSI SCSI revision: 02
-----------------------------------------------------------
root@alpha:/dev # lsmod | grep -i usb
usbhid                 30688  0
usb_storage            64704  0
scsi_mod              124872  1 usb_storage
usbcore               104316  4 usbhid,usb_storage,uhci_hcd
ide_core              125268  6 piix,usb_storage,ide_cd,ide_disk,ide_generic,via82cxxx
-------------------------------------------------------------
root@alpha:/dev # lsmod | grep -i scsi
scsi_mod              124872  2 sg,usb_storage
---------------------------------------------------------------------
root@alpha:/dev # lsscsi
[0:0:0:0]    disk    USB 2.0  Storage Device   0100  -

This is the only change I get when I unplug and plug the usb cable to the drive
tail /var/log/messages
Feb 15 21:57:16 alpha kernel: [4297903.737000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
-------------------------------------------------------------------
root@alpha:/dev # cat /proc/bus/usb/devices

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 uhci_hcd
S:  Product=VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
S:  SerialNumber=0000:00:07.3
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc= 93/900 us (10%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-10-386 uhci_hcd
S:  Product=VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
S:  SerialNumber=0000:00:07.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0402 ProdID=5621 Rev= 1.03
S:  Product=USB 2.0 Storage Device
S:  SerialNumber=00042222200000060350
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=0040 Rev= 3.00
S:  Manufacturer=Microsoft
S:  Product=Microsoft 3-Button Mouse with IntelliEye(TM)
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=10ms
---------------------------------------------------------------------------
[4294677.595000] usbcore: registered new driver usbfs
[4294677.595000] usbcore: registered new driver hub
[4294677.598000] USB Universal Host Controller Interface driver v2.2
[4294677.599000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[4294677.599000] PCI: setting IRQ 10 as level-triggered
[4294677.599000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294677.599000] uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294677.661000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294677.661000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000d400
[4294677.661000] hub 1-0:1.0: USB hub found
[4294677.661000] hub 1-0:1.0: 2 ports detected
[4294677.664000] uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294677.726000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[4294677.726000] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000d800
[4294677.726000] hub 2-0:1.0: USB hub found
[4294677.726000] hub 2-0:1.0: 2 ports detected
[4294677.830000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294678.147000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[4294679.870000] SCSI subsystem initialized
[4294679.874000] Initializing USB Mass Storage driver...
[4294679.876000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294679.876000] usb-storage: device found at 2
[4294679.876000] usb-storage: waiting for device to settle before scanning
[4294679.876000] usbcore: registered new driver usb-storage
[4294679.876000] USB Mass Storage support registered.
[4294679.902000] usbcore: registered new driver hiddev
[4294679.922000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:07.2-2
[4294679.922000] usbcore: registered new driver usbhid
[4294679.922000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294684.923000] usb-storage: device scan complete

```

---

