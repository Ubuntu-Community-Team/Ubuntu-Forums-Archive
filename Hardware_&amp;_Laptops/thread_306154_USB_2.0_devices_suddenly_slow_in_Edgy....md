---
title: "USB 2.0 devices suddenly slow in Edgy..."
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by onyxrev on 2006-11-24
Hey all.  

My machine is a Gateway MX7515 laptop running 2.6.17-10-generic on edgy.  USB was working great both in dapper and in edgy until recently.  Now all USB drives that are attached - flash drives, hard drives - all run at USB 1.0 speeds.

I can't figure out what might have changed.  The drives perform at full speed when booted into Windows.

Output of lspci shows...

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller

lsmod shows the ehci_hcd module as loaded

cat /proc/bus/usb/devices shows...

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0457 ProdID=0151 Rev= 1.00
S:  Product=USB Mass Storage Device
S:  SerialNumber=4061a6107b81ea
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 98mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=  64 Ivl=8ms


There were a couple of threads with the same issue and none of them were resolved.  Anyone have any ideas?

---

### Post by onyxrev on 2006-11-24
alright... I got it...

USB hub switched to using ohci_hcd instead of ehci_hcd for some reason...

Blacklisting ohci_hcd in /etc/default/linux-restricted-modules-common didn't seem to make a difference, so I just renamed the kernel object like so...

sudo mv /lib/modules/2.6.17-10-generic/kernel/drivers/usb/host/ohci-hcd.ko /lib/modules/2.6.17-10-generic/kernel/drivers/usb/host/ohci-hcd.bak

and then added the high speed modules to /etc/modules in the proper order:

ehci_hcd
uhci_hcd

rebooted and it's running at full speed again

I'll post this on the other threads as well.

---

