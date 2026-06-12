---
title: "USB quality up"
date: 2016-03-31
forum: Hardware
---

### Post by Anton_Kuzmin on 2016-03-31
Hello! I have HP ProBook 430 G2 with Ubuntu 14.04. With USB ports (with all 3) i have same trouble. If i plug in a wifi adapter of flash drive, i have bad work quality.
WiFi adapters has bad non-stable signal, flash drives has small speed. I think Ubuntu have troubles with usb drivers on my laptop. 
I go to [http://www.ubuntu.com/certification/hardware/201411-16204/](http://www.ubuntu.com/certification/hardware/201411-16204/) . This page have not records of usb troubles. In end of page have hardware record:
> Intel Wildcat Point-LP USB xHCI Controller
I tested my adapters and drives on other laptops with Ubuntu 14.04 - they don`t have this troubles. 
Tell please, how cat i fix it in my case?

lspci:
> 00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
07:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
09:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter


usb-device (with plugged ZyXEL external wifi adapter)
> T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=11D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.19
S:  Manufacturer=Linux 3.19.0-56-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0586 ProdID=3410 Rev=48.10
S:  Manufacturer=ZyDAS
S:  Product=ZyXEL G-202
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=zd1211rw


T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=b001 Rev=02.00
S:  Manufacturer=Realtek 
S:  Product=Bluetooth Radio 
S:  SerialNumber=00e04c000001
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb


T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=03 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=12 Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=138a ProdID=003f Rev=01.04
S:  SerialNumber=00a086f47798
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)


T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=04 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b477 Rev=96.71
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=HP HD Webcam
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.19
S:  Manufacturer=Linux 3.19.0-56-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.19
S:  Manufacturer=Linux 3.19.0-56-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8001 Rev=00.03
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


---

