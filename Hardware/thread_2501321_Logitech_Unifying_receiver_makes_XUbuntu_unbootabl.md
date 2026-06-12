---
title: "Logitech Unifying receiver makes XUbuntu unbootable"
date: 2024-10-02
forum: Hardware
---

### Post by Jackie78 on 2024-10-02
I have recently installed XUbunto 24.04 (LTS) on my old Lenovo Miix 310 netbook (Atom5) based, and found the following strange behaviour:

the device has two onboard USB ports, none of them is in any way configurable in the Lenovo BIOS (which only has very few limited options anyway), and if I connect a Logitech Unifying receiver (latest firmware installed) that came with my Logitec M705 mouse to the left USB ports, XUbuntu is reproducably failing to boot, nothing in any logs or so, so I guess that happens at very early stage.

When I plug it in on the right hand side USB port, booting works.

The effect does not appear when I run the parallely installed Windows 10 on that system.

I googled for that phenomenon, and found several similar threads, some more than 10 years old, but nobody found a solution other than switching the USB port. 

I would like to know why this happens at all. Any ideas on that?

---

### Post by him610 on 2024-10-02
> my old Lenovo Miix 310 netbook (Atom5) based
How old? 
Please show results posted between code brackets...
```
inxi -bmz
```

It could be that one of the USB ports was only wired for charging.

Added: 
Lenovo product page [https://pcsupport.lenovo.com/us/en/products/tablets/miix-series/miix-310-10icr/solutions/pd104304-product-overview-miix-310-10icr]("https://pcsupport.lenovo.com/us/en/products/tablets/miix-series/miix-310-10icr/solutions/pd104304-product-overview-miix-310-10icr")
indicates it only has one USB port...
> I/O ports	
Micro HDMI port × 1
2 in 1 slot × 1 (Micro SD/Micro SIM)
Note: Select models may not have the micro SIM card slot, please refer to the actual product.
Micro USB 2.0 port × 1

---

### Post by Jackie78 on 2024-10-04
> **him610 said:**
> How old? 
Please show results posted between code brackets...
```
inxi -bmz
```


That call gives me:

```

System:
  Kernel: 6.8.0-41-generic arch: x86_64 bits: 64
  Desktop: Xfce v: 4.18.1 Distro: Xubuntu 24.04.1 LTS (Noble Numbat)
Machine:
  Type: Detachable System: LENOVO product: 80SG v: MIIX 310-10ICR
    serial: <superuser required>
  Mobo: LENOVO model: Cavalli v: SDK0J91196 STD serial: <superuser required>
    UEFI: LENOVO v: 1HCN44WW date: 01/29/2018
Battery:
  ID-1: axp288_fuel_gauge charge: 65% condition: N/A
Memory:
  System RAM: total: 4 GiB available: 3.69 GiB used: 958.7 MiB (25.4%)
  Array-1: capacity: 8 GiB slots: 1 modules: 1 EC: None
  Device-1: ChannelA-DIMM0 type: DDR3 size: 4 GiB speed: 1600 MT/s
CPU:
  Info: quad core Intel Atom x5-Z8350 [MCP] speed (MHz): avg: 640
    min/max: 480/1920
Graphics:
  Device-1: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx
    Integrated Graphics driver: i915 v: kernel
  Display: x11 server: X.Org v: 21.1.11 driver: X: loaded: intel dri: crocus
    gpu: i915 resolution: 1280x800~60Hz
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: intel mesa v: 24.0.9-0ubuntu0.1
    renderer: Mesa Intel HD Graphics (CHV)
Network:
  Message: No PCI device data found.
Drives:
  Local Storage: total: 117.75 GiB used: 30.53 GiB (25.9%)
Info:
  Processes: 244 Uptime: 1m Shell: Bash inxi: 3.3.34

```


> 
It could be that one of the USB ports was only wired for charging.


No, both ports work in Windows, and also in XUbuntu if the receiver is just attached after booting!

> 
Added: 
Lenovo product page [https://pcsupport.lenovo.com/us/en/products/tablets/miix-series/miix-310-10icr/solutions/pd104304-product-overview-miix-310-10icr](https://pcsupport.lenovo.com/us/en/products/tablets/miix-series/miix-310-10icr/solutions/pd104304-product-overview-miix-310-10icr)
indicates it only has one USB port...

This information is definitely not correct, I assume Lenovo is referring to the tablet device itself. The main keyboard that comes with the device and which is detachable has two USB ports, one on the right and one on the left hand side of the keyboard. How these are internally wired, I don't know.


Here is some more USB related output I get using common tools, none of which really helps me, but which may be of use for the experts?

```

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 258a:1015 SIPODEV USB Composite Device
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh= 7
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=06.08
S:  Manufacturer=Linux 6.8.0-41-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=258a ProdID=1015 Rev=01.05
S:  Manufacturer=SIPODEV
S:  Product=USB Composite Device
S:  SerialNumber=S9580-7232-US-160120
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=8ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=4ms

T:  Bus=01 Lev=01 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=480  MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0608 Rev=85.36
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms

T:  Bus=01 Lev=02 Prnt=03 Port=03 Cnt=01 Dev#=  6 Spd=12   MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c52b Rev=12.11
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=8ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=2ms
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=  32 Ivl=2ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=06.08
S:  Manufacturer=Linux 6.8.0-41-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms




udevadm when connecting too the right hand USB port which is working fine also during startup!

udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[503.743609] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4 (usb)
KERNEL[503.752931] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4 (usb)
KERNEL[503.753262] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.0 (usb)
KERNEL[503.754854] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.0/0003:046D:C52B.000F (hid)
KERNEL[503.755195] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.0 (usb)
KERNEL[503.755939] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.1 (usb)
KERNEL[503.760234] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.1/0003:046D:C52B.0010 (hid)
KERNEL[503.760514] add      /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
KERNEL[503.760706] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.1 (usb)
KERNEL[503.760903] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2 (usb)
KERNEL[503.763334] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011 (hid)
KERNEL[503.763919] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/usbmisc/hiddev1 (usbmisc)
KERNEL[503.764157] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/hidraw/hidraw2 (hidraw)
UDEV  [503.781652] add      /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
KERNEL[503.836722] remove   /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [503.845612] remove   /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
KERNEL[503.868291] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011 (hid)
KERNEL[503.868909] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2 (usb)
KERNEL[503.869334] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4 (usb)
KERNEL[503.871328] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012 (hid)
KERNEL[503.877692] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/input/input30 (input)
KERNEL[503.878736] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/input/input30/mouse2 (input)
KERNEL[503.878851] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/input/input30/event12 (input)
KERNEL[503.878959] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/hidraw/hidraw3 (hidraw)
KERNEL[503.880504] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012 (hid)
KERNEL[503.905337] add      /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [503.909764] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4 (usb)
UDEV  [503.911813] add      /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [503.928966] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4 (usb)
UDEV  [503.941258] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.0 (usb)
UDEV  [503.955199] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2 (usb)
UDEV  [503.955956] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.0/0003:046D:C52B.000F (hid)
UDEV  [503.968258] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011 (hid)
UDEV  [503.968427] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.1 (usb)
UDEV  [503.977211] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.0 (usb)
KERNEL[503.983803] remove   /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [503.992534] remove   /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [503.996786] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/usbmisc/hiddev1 (usbmisc)
UDEV  [504.001893] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.1/0003:046D:C52B.0010 (hid)
UDEV  [504.009647] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.1 (usb)
UDEV  [504.622276] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/hidraw/hidraw2 (hidraw)
UDEV  [504.629554] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011 (hid)
UDEV  [504.636451] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2 (usb)
UDEV  [504.667396] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4 (usb)
UDEV  [504.679936] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012 (hid)
UDEV  [504.710284] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/input/input30 (input)
UDEV  [504.732451] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/input/input30/mouse2 (input)
UDEV  [504.766991] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/input/input30/event12 (input)
UDEV  [505.325853] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/hidraw/hidraw3 (hidraw)
UDEV  [505.338261] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012 (hid)
KERNEL[510.271156] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/power_supply/hidpp_battery_3/wakeup35 (wakeup)
KERNEL[510.271428] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/power_supply/hidpp_battery_3/hwmon6 (hwmon)
KERNEL[510.281739] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/power_supply/hidpp_battery_3 (power_supply)
UDEV  [510.314666] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/power_supply/hidpp_battery_3/wakeup35 (wakeup)
UDEV  [510.316458] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/power_supply/hidpp_battery_3/hwmon6 (hwmon)
UDEV  [510.327197] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/power_supply/hidpp_battery_3 (power_supply)
KERNEL[510.367367] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/power_supply/hidpp_battery_3 (power_supply)
UDEV  [510.379932] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.2/0003:046D:C52B.0011/0003:046D:406D.0012/power_supply/hidpp_battery_3 (power_supply)


udevadm when connecting too the left hand USB port which is not working during startup!
udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[545.102475] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1 (usb)
KERNEL[545.112849] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1 (usb)
KERNEL[545.113442] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.0 (usb)
KERNEL[545.116663] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.0/0003:046D:C52B.0013 (hid)
KERNEL[545.117203] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.0 (usb)
KERNEL[545.117467] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.1 (usb)
KERNEL[545.119916] add      /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
KERNEL[545.120149] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.1/0003:046D:C52B.0014 (hid)
KERNEL[545.120920] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.1 (usb)
KERNEL[545.121165] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2 (usb)
KERNEL[545.125215] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015 (hid)
KERNEL[545.126141] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/usbmisc/hiddev1 (usbmisc)
KERNEL[545.127436] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/hidraw/hidraw2 (hidraw)
UDEV  [545.144297] add      /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
KERNEL[545.197480] remove   /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [545.207297] remove   /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
KERNEL[545.231373] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015 (hid)
KERNEL[545.231673] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2 (usb)
KERNEL[545.231983] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1 (usb)
KERNEL[545.234767] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016 (hid)
KERNEL[545.241465] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/input/input31 (input)
KERNEL[545.242684] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/input/input31/mouse2 (input)
KERNEL[545.242937] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/input/input31/event12 (input)
KERNEL[545.243579] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/hidraw/hidraw3 (hidraw)
KERNEL[545.245357] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016 (hid)
KERNEL[545.268086] add      /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [545.274962] add      /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [545.277708] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1 (usb)
UDEV  [545.294986] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1 (usb)
UDEV  [545.313083] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.0 (usb)
UDEV  [545.316249] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.1 (usb)
UDEV  [545.327259] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.1/0003:046D:C52B.0014 (hid)
UDEV  [545.334873] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.0/0003:046D:C52B.0013 (hid)
UDEV  [545.337862] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.1 (usb)
KERNEL[545.346827] remove   /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [545.351079] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2 (usb)
UDEV  [545.352534] remove   /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/808622C1:01/OVTI2680:01/wakeup/wakeup35 (wakeup)
UDEV  [545.355541] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.0 (usb)
UDEV  [545.368584] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015 (hid)
UDEV  [545.375875] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/usbmisc/hiddev1 (usbmisc)
UDEV  [546.008995] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/hidraw/hidraw2 (hidraw)
UDEV  [546.017953] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015 (hid)
UDEV  [546.027526] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2 (usb)
UDEV  [546.058320] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1 (usb)
UDEV  [546.070379] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016 (hid)
UDEV  [546.106347] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/input/input31 (input)
UDEV  [546.136846] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/input/input31/mouse2 (input)
UDEV  [546.173367] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/input/input31/event12 (input)
UDEV  [546.756553] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/hidraw/hidraw3 (hidraw)
UDEV  [546.763856] bind     /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016 (hid)
KERNEL[548.761575] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/power_supply/hidpp_battery_4/wakeup35 (wakeup)
KERNEL[548.761775] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/power_supply/hidpp_battery_4/hwmon6 (hwmon)
KERNEL[548.772795] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/power_supply/hidpp_battery_4 (power_supply)
UDEV  [548.788953] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/power_supply/hidpp_battery_4/wakeup35 (wakeup)
UDEV  [548.796270] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/power_supply/hidpp_battery_4/hwmon6 (hwmon)
UDEV  [548.805543] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/power_supply/hidpp_battery_4 (power_supply)
KERNEL[548.835202] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/power_supply/hidpp_battery_4 (power_supply)
UDEV  [548.849175] change   /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.1/1-4.1:1.2/0003:046D:C52B.0015/0003:046D:406D.0016/power_supply/hidpp_battery_4 (power_supply)



```

---

