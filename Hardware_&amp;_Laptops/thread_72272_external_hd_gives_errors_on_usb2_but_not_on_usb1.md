---
title: "external hd gives errors on usb2 but not on usb1"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by progster on 2005-10-05
I just bought a pci usb2.0 (full speed)  card which seems to work perfectly, however my external hard drive seems to fail when I connect it via usb2.0 (the pci card works though). I get the following dmesg output:

> 
usb 5-2: new high speed USB device using ehci_hcd and address 3
SCSI subsystem initialized
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
  Vendor: MAXTOR 6  Model: L080J4            Rev: 0000
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
SCSI device sda: 156355584 512-byte hdwr sectors (80054 MB)
sda: assuming drive cache: write through
SCSI device sda: 156355584 512-byte hdwr sectors (80054 MB)
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0:SCSI error : <0 0 0 0 > return code = 0x70000
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0


Same disk gives no errors on my onboard usb1.1:
> usb 1-1: new full speed USB device using uhci_hcd and address 2
usb 1-1: not running at top speed; connect to a high speed hub
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: MAXTOR 6  Model: L080J4            Rev: 0000
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 156355584 512-byte hdwr sectors (80054 MB)
sda: assuming drive cache: write through
SCSI device sda: 156355584 512-byte hdwr sectors (80054 MB)
sda: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: p1
Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete

Does anyone have any idea of how this happens and what I can do to fix it? Any help is greatly appreciated!

---

### Post by progster on 2005-10-06
I have searched quite a bit here, but haven't find any realy solution yet (well most "solutions" suggested to modprobe scsi_mod, but that doens't seem to help)

---

### Post by progster on 2005-10-07
doesn't anyone have any idea?

---

### Post by taygan on 2005-10-18
can you enable DMA?

[http://www.ubuntuforums.org/showthread.php?t=77948&highlight=sudo+hdparm](http://www.ubuntuforums.org/showthread.php?t=77948&highlight=sudo+hdparm)

sudo hdparm -d 1 /dev/sda ( <-enter your device there )

---

### Post by progster on 2005-10-23
[QUOTE=taygan]can you enable DMA?

[http://www.ubuntuforums.org/showthread.php?t=77948&highlight=sudo+hdparm](http://www.ubuntuforums.org/showthread.php?t=77948&highlight=sudo+hdparm)

sudo hdparm -d 1 /dev/sda ( <-enter your device there )[/QUOTE]
```
 $ sudo hdparm -d 1 /dev/sda1

/dev/sda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument

```

Further information:
```

$cat /proc/bus/usb/devices

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.10-5-k7 ehci_hcd
S:  Product=VIA Technologies, Inc. USB 2.0
S:  SerialNumber=0000:00:0a.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04b4 ProdID=6830 Rev= 0.01
S:  Manufacturer=
S:  Product=
S:  SerialNumber=D
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=86(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms

<snip>

```

Any suggestions?

---

### Post by progster on 2005-11-13
well that's kind of dissapointing :(

---

