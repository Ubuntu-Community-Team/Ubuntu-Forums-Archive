---
title: "ZTE cdma wll under ubuntu with cp2102 uart"
date: 2009-09-12
forum: Hardware
---

### Post by Nole1 on 2009-09-12
Hello,
I have this model of modem and this is the only way of communicating with the rest of the world from Sahara where I am at the moment. This wall (wireless land line) and I do not know how to make it working under Ubuntu 9.04. Downloaded CP 2102 UART drivers from the net hoping that this will recognize my device but it failed without any results. Please somebody help.

---

### Post by Nole1 on 2009-09-14
Please again, anybody?
I have tried allmost everything I found on the net and here are the result... Anybody reading this Please help...

Here is the result of the file when entering the command 

cat /proc/bus/usb/devices
...
T:  Bus=06 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=10c4 ProdID=ea60 Rev= 1.00
S:  Manufacturer=Silicon Labs
S:  Product=CP2102 USB to UART Bridge Controller
S:  SerialNumber=0001
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
...

and here is the file cdma.conf what I made for this modem

#[Dialer Defaults]
# New PPPD=yes
[Modem0]
Modem Type = USB Modem
Modem = /dev/ttyUSB0
Baud = 230400
Setvolume = 0
Dial Command = ATDT
Init1 = ATZ
Flow control=Hardware(CRTSCTS)
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
[Dialer cdma]
Username = â€cdmaâ€
Password = â€cdmaâ€
Phone = #777
Stupid Mode = 1 
Inherits=Modem0
# Ask Password = on

here is the result of command 

lsusb

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Here is the result of command 
modprobe acm vendor-0x10c4 product=0xea60
FATAL: Module acm not found.

I do not have more ideas and it is still not working... Please help me somebody

---

