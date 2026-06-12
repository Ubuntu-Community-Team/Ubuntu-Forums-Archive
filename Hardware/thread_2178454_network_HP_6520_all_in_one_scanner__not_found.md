---
title: "network HP 6520 all in one scanner  not found"
date: 2013-10-03
forum: Hardware
---

### Post by pdcooper on 2013-10-03
ive tried the HPLIP set up  but its fails to find the scanner. 
When i plugged the USB cable in, the computer  recognised the printer and it is listed in cups  both as a USB  print and a network printe[SIZE=2][FONT=arial]r. socket://192.168.1.67:9100[/FONT][/SIZE]

its on the network
```
Nmap scan report for HP01D6AC.home (192.168.1.67)
Host is up (0.0094s latency).
Not shown: 984 closed ports
PORT     STATE SERVICE
80/tcp   open  http
139/tcp  open  netbios-ssn
443/tcp  open  https
445/tcp  open  microsoft-ds
631/tcp  open  ipp
6839/tcp open  unknown
7435/tcp open  unknown
8080/tcp open  http-proxy
8089/tcp open  unknown
9100/tcp open  jetdirect
9101/tcp open  jetdirect
9102/tcp open  jetdirect
9110/tcp open  unknown
9111/tcp open  DragonIDSConsole
9220/tcp open  unknown
9290/tcp open  unknown
MAC Address: D8:9D:67:01:D6:AC (Unknown)

```
its not listed in hplip. I plug te USB in and  select wireless or network/ethernet/wireless then device discovery doesnt list anything 

but xsane cant find it 
hp-setup gives this 
```
# hp-setup


HP Linux Imaging and Printing System (ver. 3.13.4)
Printer/Fax Setup Utility ver. 9.0


Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Searching on USB bus...
error: No devices found on bus: usb


Done.

```
in spite of 
```
$ lsusb | grep Pac
Bus 001 Device 006: ID 03f0:af11 Hewlett-Packard 

```

so how can i tell it where the printer/scanner is ?

---

