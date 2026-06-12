---
title: "usb device driver problem"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by g.a. on 2007-12-19
Hi,

I'm having troubles with a usb device. It is an acquisition device for which someone developed some API and drivers ([ftp://lx10.tx.ncsu.edu/pub/Linux/drivers](ftp://lx10.tx.ncsu.edu/pub/Linux/drivers)). I'm interested in the API that makes use of the Linux hiddev driver.

My problem is quite basic, from the readme file of the API I have

"In order to use the hiddev driver, one must include hiddev support in
the Linux kernel.  This is generally done with most of the major
distributions.  Each HID interface is associated with a device node,
usually /dev/usb/hiddev[0-15], although the location of these files
could change. "

The libraries seem to be there (libhid-dev, libhid0) but not the directory /dev/usb/hiddev

Moreover, the command cat /proc/bus/usb/devices returns

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=09db ProdID=007a Rev= 1.00
S:  Manufacturer=MCC
S:  Product=USB-1208LS
S:  SerialNumber=012B0707
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
E:  Ad=01(O) Atr=03(Int.) MxPS=   8 Ivl=10ms

where it can be noticed that no driver is associated with the device. 

the command lsusb returns

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 09db:007a Measurement Computing Corp. PMD-1208LS
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

so the device is there. the command dmesg returns

[15534.168000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[15534.348000] usb 2-1: configuration #1 chosen from 1 choice

so when i run the test program that uses the API it tells me that no device has been found.

any suggestion?

thanks in advance,
g.

---

