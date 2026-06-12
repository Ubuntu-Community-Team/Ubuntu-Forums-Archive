---
title: "Can't get External USB HDD to Work in Ubuntu 22.04"
date: 2022-07-16
forum: Hardware
---

### Post by criageek on 2022-07-16
I picked up a Seagate 5TB USB HDD to use for doing backups and cannot get it to work on my primary computer, running Ubuntu 22.04.  It works fine on a Windows box and it works fine on another Ubuntu box, but not on the one it need it to work on.  It doesn't show up in Files, and it doesn't show up in the Disks utility or GParted.  I do see it when I run lsusb

```
Bus 002 Device 004: ID 18e3:9102 Fitipower Integrated Technology Inc Multi Card Reader
Bus 002 Device 003: ID 062a:4101 MosArt Semiconductor Corp. Wireless Keyboard/Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0bc2:2037 Seagate RSS LLC Expansion HDD
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 17ef:602d Lenovo Black Silk Keyboard
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

 or usb-devices.

```
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=5000 MxCh= 0
D:  Ver= 3.20 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 9 #Cfgs=  1
P:  Vendor=0bc2 ProdID=2037 Rev=19.01
S:  Manufacturer=Seagate
S:  Product=Expansion HDD
S:  SerialNumber=00000000NACC9KTG
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=896mA
I:  If#= 0 Alt= 1 #EPs= 4 Cls=08(stor.) Sub=06 Prot=62 Driver=uas
E:  Ad=01(O) Atr=02(Bulk) MxPS=1024 Ivl=0ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=1024 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=1024 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=1024 Ivl=0ms

```

Other USB devices are detected and work properly.  The USB HDD is plugged into a USB 3.0 port and I've tried both 3.0 ports on this pc.

Any ideas??

Thanks,
Rich

---

### Post by him610 on 2022-07-16
> [COLOR="#FF0000"]MxPwr=896mA[/COLOR]
If this reflects the current draw of your external USB HDD then that is may be the problem. 
It has been awhile now, and I may be wrong, but I was under the impression that USB ports were capable of only providing a maximum of 500mA.

---

### Post by criageek on 2022-07-16
Thanks him610 - when researching this earlier I came across a thread that said USB 3.0 ports are capable of providing 900mA, and this is plugged into a USB 3.0 port.  Plus, when I tried it on another PC (and it worked perfectly) I'm pretty sure that was a USB 2.0 port.

Rich

---

### Post by Autodave on 2022-07-16
How many other things do you have plugged into USB ports?  Is this plugged into a hub?  Is the hub powered or non-powered?

You could also have a weak power supply.

---

### Post by criageek on 2022-07-17
I'm not using any sort of external hub...just the onboard ports.  When I tried this on another computer, and it worked, it was through an external, powered hub.  So I'll bring that to this PC and give it a try later when I have a couple of minutes.  The only USB devices I am using are the keyboard and mouse, and neither is using a USB 3.0 port.

Thanks!

Rich

---

### Post by criageek on 2022-07-17
I just moved the USB 2.0 hub from the other computer to this one and connected the Seagate drive to it...it works!  So I'll pick up a USB 3.0 hub and should be good to go.  Than ks for the help  ;)

Rich

---

