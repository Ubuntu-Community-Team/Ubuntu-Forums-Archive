---
title: "Mapping a device to a COM port in WINE"
date: 2012-11-24
forum: Hardware
---

### Post by PapaNerd on 2012-11-24
Configuration:
Ubuntu 10.04.4 LTS
USB-connected Arduino board recognized on /dev/ttyACM0 (as expected)
Windoze app running under WINE which should talk to the Arduino board

Output from usb-devices command:

T: Bus=02 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#= 7 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=02(commc) Sub=00 Prot=00 MxPS= 8 #Cfgs= 1
P: Vendor=2341 ProdID=0001 Rev=00.01
S: Manufacturer=Arduino ([www.arduino.cc](www.arduino.cc))
S: Product=Arduino Uno
S: SerialNumber=74136333932351C0B162
C: #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=100mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I: If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

Problem Description:
The app searches from COM 1 through COM 9, but cannot find the Arduino board.  I created symbolic links in the /dev and ~/.wine/dosdevices directories per other forum posts, but these seem to be ignored.

Question:
How does one configure WINE so that /dev/ttyACM0 maps (for example) to COM 2?

---

### Post by vidyadhari on 2013-08-12
Hi, 
       I too have a similar problem. I'm using a software called Proview through wine on ubuntu 12.04 LTS and the usb needs to be detected as COM1 -COM9. I have created a symbolic link as 
"ln -s /dev/ttyUSB0  /.wine/dosdevices/dosdevices/COM1"  (as my device is detected on ttyUSB0) and I guess the link is successfully created as I found a file COM1(of type link to character devices) in the folder /.wine/dosdevices/
But I get an error message saying "connection to remote terminal failed :media failure or device unavailable" when I try to connect with the software.
Please share the solution in case you have found any.
Thanks in advance

---

