---
title: "External USB drives not recognised"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by devnulljp on 2005-11-06
Been googling around for a while to try to resolve this issue, but no luck yet. I have several external USB drives - a pen drive, a 250 GB ext HDD, and an 80 GB ext HDD - none of these are recognised on my plain vanilla Ubuntu 5.10 install.
lsusb doesn't list them at all
Nothing is created in /dev/ (no sda etc.)
 
All drives work fine, as do cables (all OK under old suse and gentoo installs, dual boot into win2000, and when booted from Knoppix DVD - although they don't work when booted from either ubuntu breezy install or live CD).

usb_storage module seems to be loaded
ehci_hcd seems to be loaded

lsusb output:
```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

So my usb mouse is working fine - no drives show up

tail /var/log/messages:
```
Nov  6 17:54:40 localhost kernel: [4305292.319000] usb 4-1: new high speed USB device using ehci_hcd and address 47
Nov  6 17:54:40 localhost kernel: [4305292.536000] usb 4-3: new high speed USB device using ehci_hcd and address 48
Nov  6 17:54:42 localhost kernel: [4305294.606000] usb 4-3: new high speed USB device using ehci_hcd and address 60
Nov  6 17:54:45 localhost kernel: [4305297.352000] usb 4-3: new high speed USB device using ehci_hcd and address 76
Nov  6 17:54:46 localhost kernel: [4305298.256000] usb 4-1: new high speed USB device using ehci_hcd and address 80
Nov  6 17:54:47 localhost kernel: [4305298.851000] usb 4-3: new high speed USB device using ehci_hcd and address 83
Nov  6 17:54:49 localhost kernel: [4305300.756000] usb 4-1: new high speed USB device using ehci_hcd and address 94
```

dmesg gives me this:
```
[4305040.006000] usb 4-1: new high speed USB device using ehci_hcd and address 7[4305040.446000] usb 4-1: new high speed USB device using ehci_hcd and address 9[4305041.696000] usb 4-1: new high speed USB device using ehci_hcd and address 16
[4305042.068000] usb 4-1: new high speed USB device using ehci_hcd and address 18
[4305042.946000] usb 4-1: new high speed USB device using ehci_hcd and address 23
[4305045.196000] usb 4-1: new high speed USB device using ehci_hcd and address 36
[4305045.419000] usb 4-3: new high speed USB device using ehci_hcd and address 37
[4305047.696000] usb 4-1: new high speed USB device using ehci_hcd and address 50
[4305048.446000] usb 4-1: new high speed USB device using ehci_hcd and address 54
```

So it looks like there's something happening on my usb buses, just nothing I can use to get at my drives.

cat /proc/bus/usb/devices

```
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-686 ehci_hcd
S:  Product=Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-686 uhci_hcd
S:  Product=Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
S:  SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=118/900 us (13%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-686 uhci_hcd
S:  Product=Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c50e Rev=25.00
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr= 70mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-686 uhci_hcd
S:  Product=Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms
```

Anyone have any ideas? 
What next? 

FWIW, I'm on a Thinkpad T41 with a docking station. Originally, drives were plugged into the 4 ports on the dock, but as they weren't working I've pulled everything from the dock and have only the USB mouse and the 80GB HDD plugged directly into the 2 ports on the body of the notebook. Ideally, I'd go back to using the ports on the dock (which worked fine under suse, gentoo and knoppix).
Any pointers appreciated.

---

### Post by LoicMinier on 2006-07-09
Hi,

I've got the very same problem, and tried quite a lot of things already.

I suspect it's an interrupt handling issue, so I tried:
- passing acpi=noirq on the kernel command line
- passing noapic on the kernel command line
- unloading drivers sharing the same interrupt (mostly yenta_socket + ath_pci + uhci_hcd)

... to no luck.

I searched the Kernel bugzilla, but couldn't find anyone with the same bug there (that is, with the EPIPE and ETIMEDOUT and the devices appearing in loop).

Did you find a solution yet?

Bye,

---

