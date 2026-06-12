---
title: "usb port not working on ubuntu."
date: 2014-07-17
forum: Hardware
---

### Post by amr-elfiky on 2014-07-17
i got a new laptop ([COLOR=#545454][FONT=arial]**Toshiba Satellite**[/FONT][/COLOR][COLOR=#545454][FONT=arial] C50-[/FONT][/COLOR][COLOR=#545454][FONT=arial]**A538**[/FONT][/COLOR][COLOR=#545454][FONT=arial] ) and after installing ubuntu 14.04 ,i noticed that the usb ports on the right don't always work .it never happens on windows 8 so i guess it's not a hardware problem .i have to restart the laptop 3 or 4 times before i get the usb mouse to work .it's completely random .it's hard to know after how many reboots it's going to work .
i think it can't be the mouse as i tried a flash drive in the same usb ports and it wasn't identified .can anyone help me ,please ?[/FONT][/COLOR]

---

### Post by varunendra on 2014-07-19
Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
lsusb
usb-devices
```
..to show us what kind of USB controllers and drivers you have.

And does your laptop's BIOS have a feature called "IOMMU"?

---

### Post by amr-elfiky on 2014-07-27
sorry for being late  to reply .i had no internet connection for a while .
here is the output .
```
amr@amr-Satellite-C50-A538:~$ lsusbBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b3b1 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 0930:0220 Toshiba Corp. 
Bus 003 Device 007: ID 1c4f:0003 SiGma Micro HID controller
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
amr@amr-Satellite-C50-A538:~$ usb-devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.01 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=058f ProdID=6366 Rev=01.00
S:  Manufacturer=Generic
S:  Product=Flash Card Reader/Writer
S:  SerialNumber=058F63666485
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b3b1 Rev=57.16
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=TOSHIBA Web Camera - HD
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1c4f ProdID=0003 Rev=01.10
S:  Manufacturer=SIGMACHIP
S:  Product=Usb Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid


T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0930 ProdID=0220 Rev=00.02
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
amr@amr-Satellite-C50-A538:~$ 



```
i don't really know what this means "IOMMU"

---

### Post by varunendra on 2014-07-27
The mouse is present in the above outputs. Please post the same outputs from the state when the problem occurs. Apart from the above outputs, also post the outputs of -
```
lsmod | egrep 'hid|psmouse'
xinput
```..when the problem occurs.

IOMMU is a feature in some BIOS programs that imposes some additional security controls on Input/output devices. If your BIOS doesn't show this name anywhere, forget it.

---

### Post by skor-roks on 2014-07-27
Hello,

Iwas having the same problem. I just installed ubuntu on my latpop and the USB ports wasn't working. I found this thread here: [http://ubuntuforums.org/showthread.php?t=1938120](http://ubuntuforums.org/showthread.php?t=1938120)

and with this command line and a reboot the USB ports start working, maybe will help you too.

```
sudo dpkg-reconfigure xserver-xorg
```

Regards.

---

### Post by amr-elfiky on 2014-07-29
thanks,[[COLOR=#000000]skor-roks[/COLOR]]("http://ubuntuforums.org/member.php?u=1936515")[COLOR=#000000] .but my problem is that the usb ports stop working sometimes not always .maybe once i switch the laptop on ,maybe after hibernating ,at anytime .it looks like the thread up there  is for usb ports that don't function at all .thanks anyway .[/COLOR]

all right , i just suspended the laptop and when i opened it again the usb was not working .it was working before i suspend .the usb mouse is like always with the light on but not responding .
here is the output ```
amr@amr-Satellite-C50-A538:~$ lsusbBus 002 Device 006: ID 0930:0220 Toshiba Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b3b1 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
amr@amr-Satellite-C50-A538:~$ usb-devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.01 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=058f ProdID=6366 Rev=01.00
S:  Manufacturer=Generic
S:  Product=Flash Card Reader/Writer
S:  SerialNumber=058F63666485
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b3b1 Rev=57.16
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=TOSHIBA Web Camera - HD
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0930 ProdID=0220 Rev=00.02
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.13
S:  Manufacturer=Linux 3.13.0-29-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
amr@amr-Satellite-C50-A538:~$ 



```

here is the other outputs .
```
amr@amr-Satellite-C50-A538:~$ lsmod | egrep 'hid|psmouse'mac_hid                13037  0 
hid_generic            12492  0 
psmouse                91033  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
amr@amr-Satellite-C50-A538:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=9	[slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                 	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
amr@amr-Satellite-C50-A538:~$ 





```

sorry[SIZE=1],[SIZE=2]varunendra, but tell me how to  look for this [/SIZE][/SIZE]IOMMU in BIOS ,please .

---

### Post by varunendra on 2014-07-29
> **amr-elfiky said:**
> sorry, varunendra, but tell me how to  look for this IOMMU in BIOS ,please .

Hard to tell without knowing the layout of your BIOS. By its nature, it should be under "Advance BIOS Settings", or "Peripherals", or "Onboard Device Settings" etc. These are provided by different names, under different sections in different BIOS programs. But like I said, not all BIOS programs have this feature, only a few modern ones have. So it is quite possible that it doesn't exist in your BIOS at all.

But on another thought, I think we can try an old workaround that tries to detach the USB driver from the USB bus, and re-attaches it in an attempt to reset the bus and connected devices without rebooting.

To try that, I need to know the exact PCI addresses of the USB buses. Please post back the output of -
```
lspci
cat /proc/bus/input/devices
```
..while the mouse is detected and working.

---

### Post by amr-elfiky on 2014-08-01
there it is ..
```
amr@amr-Satellite-C50-A538:~$ lspci00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 7 Series Chipset Family 4-port SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.5 IDE interface: Intel Corporation 7 Series Chipset Family 2-port SATA Controller [IDE mode] (rev 04)
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1)
08:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Qualcomm Atheros QCA8172 Fast Ethernet (rev 10)
amr@amr-Satellite-C50-A538:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7


I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input11
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=9
B: EV=b
B: KEY=6420 0 30000 0 0 0 0 0 0 0 0
B: ABS=2608000 11000003


I: Bus=0003 Vendor=04f2 Product=b3b1 Version=5716
N: Name="TOSHIBA Web Camera - HD"
P: Phys=usb-0000:00:1a.0-1.3/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input12
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:38/LNXVIDEO:00/input/input13
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input14
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input17
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input16
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input15
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10


I: Bus=0003 Vendor=1c4f Product=0003 Version=0110
N: Name="SIGMACHIP Usb Mouse"
P: Phys=usb-0000:00:14.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input19
U: Uniq=
H: Handlers=mouse1 event11 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10


amr@amr-Satellite-C50-A538:~$ 



```

---

### Post by varunendra on 2014-08-01
> **amr-elfiky said:**
> ```
**[COLOR="#0000CD"]00:14.0[/COLOR]** USB controller: Intel Corporation 7 Series/C210 Series Chipset Family **[COLOR="#0000CD"]USB xHCI Host Controller[/COLOR]** (rev 04)
....
....
I: Bus=0003 Vendor=1c4f Product=0003 Version=0110
N: Name="**SIGMACHIP Usb Mouse**"
P: Phys=usb-0000:00:14.0-1/input0
S: Sysfs=/devices/pci0000:00/**[COLOR="#0000CD"]0000:00:14.0[/COLOR]**/usb3/3-1/3-1:1.0/input/input19

```

It seems your mouse is currently connected to a USB 3 port? Usually USB 2 is considered less problematic in case there is problem with USB.

Anyway, please try this -
```
echo -n "0000:00:14.0" | sudo tee /sys/bus/pci/drivers/xhci_hcd/unbind
echo -n "0000:00:14.0" | sudo tee /sys/bus/pci/drivers/xhci_hcd/bind
```
..for the USB 3 port/hub.

Or,
```
echo -n "0000:**00:1a.0**" | sudo tee /sys/bus/pci/drivers/**ehci_hcd**/unbind
echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/bind
```
or,
```
echo -n "0000:**00:1d.0**" | sudo tee /sys/bus/pci/drivers/**ehci_hcd**/unbind
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/bind
```
..for USB 2 ports/buses in your laptop.

This simply removes the USB drivers xhci_hcd or ehci_hcd from USB 3 or USB 2 hubs respectively, then reattaches them, thus simulating a logical reset of the entire hub.

**Please Note** that this causes ALL the devices connected to the target hub be disconnected > reconnected. For example, if you reset the hub at PCI address "**00:1a.0**", then the internal webcam (which is connected to this hub) will also get disconnected for a moment. Will be reconnected with the "....bind" command, but IF it was in use at that time, its dedicated driver "uvcvideo" and/or the program that was using it *may* get confused sometimes, requiring you to either restart the program that was using it (e.g. cheese) or reboot the laptop altogether for it to work again.

--

---

### Post by amr-elfiky on 2014-08-01
this is embarrassing ! i don't really know which usb port is the 2 and which one is the 3.the manual that came with the device doesn't identify them properly .but what i do know is that i have 3 usb ports and 2 of them are usb 2 .so which one is the 3 ?  that's the twist !! 
anyway it's almost always i'm attaching the mouse to the same usb port so ,im guessing that's the  3 .
so here is the output .
```
amr@amr-Satellite-C50-A538:~$ echo -n "0000:00:14.0" | sudo tee /sys/bus/pci/drivers/xhci_hcd/unbind[sudo] password for amr: 
0000:00:14.0amr@amr-Satellite-C50-A538:~$ echo -n "0000:00:14.0" | sudo tee /sysvers/xhci_hcd/bind
0000:00:14.0amr@amr-Satellite-C50-A538:~$ 



```

and that's the output for the usb2
```
amr@amr-Satellite-C50-A538:~$ echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind[sudo] password for amr: 
tee: /sys/bus/pci/drivers/ehci_hcd/unbind: No such file or directory
0000:00:1a.0amr@amr-Satellite-C50-A538:~$ echo -n "0000:00:1a.0" | sudo tee /sysvers/ehci_hcd/bind
tee: /sys/bus/pci/drivers/ehci_hcd/bind: No such file or directory
0000:00:1a.0amr@amr-Satellite-C50-A538:~$ 



```

the output of the other command for usb2
```
amr@amr-Satellite-C50-A538:~$ echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind[sudo] password for amr: 
tee: /sys/bus/pci/drivers/ehci_hcd/unbind: No such file or directory
0000:00:1d.0amr@amr-Satellite-C50-A538:~$ echo -n "0000:00:1d.0" | sudo tee /sysvers/ehci_hcd/bind
tee: /sys/bus/pci/drivers/ehci_hcd/bind: No such file or directory
0000:00:1d.0amr@amr-Satellite-C50-A538:~$ 



```

---

### Post by varunendra on 2014-08-02
The plastic base-plate of USB-3 should be blue, while it is black for USB-1/2. Like this image -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=255210&stc=1&d=1406968999[/IMG]

And it seems the guess about the path of the USB 2 drivers was not correct. Let's find out the correct path. Please post back the output of -
```
find /sys -maxdepth 6 -iname "0000:00:1a.0" 2>/dev/null
find /sys -maxdepth 6 -iname "0000:00:1d.0" 2>/dev/null
```


But the USB 3 related command completed successfully. If your mouse was connected to it at the time, it should have been reset (at least logically).

---

### Post by amr-elfiky on 2014-08-08
damn ,you're good ,Varunedra ! i never noticed the blue plate before .
there is the output .
```
amr@amr-Satellite-C50-A538:~$ find /sys -maxdepth 6 -iname "0000:00:1a.0" 2>/dev/null/sys/bus/pci/devices/0000:00:1a.0
/sys/bus/pci/drivers/ehci-pci/0000:00:1a.0
/sys/devices/pci0000:00/0000:00:1a.0
amr@amr-Satellite-C50-A538:~$ find /sys -maxdepth 6 -iname "0000:00:1d.0" 2>/dev/null
/sys/bus/pci/devices/0000:00:1d.0
/sys/bus/pci/drivers/ehci-pci/0000:00:1d.0
/sys/devices/pci0000:00/0000:00:1d.0
amr@amr-Satellite-C50-A538:~$ 



```

---

### Post by varunendra on 2014-08-08
Thanks for recognizing my talent (in recognizing the obvious :lol: )

To try the reset on USB-2 ports, please browse to the following locations and confirm if there are two files named "bind" and "unbind" there -
/sys/bus/pci/drivers/ehci-pci/0000:00:1a.0
/sys/bus/pci/drivers/ehci-pci/0000:00:1d.0

If yes, you can try the following commands, modified for "ehci-pci" -
```
echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/unbind
echo -n "0000:00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/bind
```
and
```
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/unbind
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/bind
```

But like I said earlier, if your mouse was connected to USB3 port, it should have been reset at the previous attempt, since the path (and hence the command) pertaining to USB-3 were apparently correct. Maybe you can have better luck with a USB-2 port.

If it were happening only with the mouse, I would have suspected and tried something else. But since you mentioned it happens with USB flash drive as well, it may indeed be something wrong with the USB drivers or underlying support mechanism in Ubuntu/Linux.

---

