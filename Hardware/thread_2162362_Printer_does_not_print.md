---
title: "Printer does not print"
date: 2013-07-14
forum: Hardware
---

### Post by stookin on 2013-07-14
hello everyone

I have an HP officejet G55 printer connected with USB to ubuntu but when I try to print, it does not print.
When I type ```
lsusb
``` in terminal, it does detect the printer. Output below:
```
Bus 004 Device 002: ID 03f0:0011 Hewlett-Packard OfficeJet G55
```

I tried to go to hardware in system settings, but it seems like it's only for network printers.

I don't know what to do, I'm stuck.:confused:

---

### Post by kc1di on 2013-07-14
Hi, 
That printer should be able to work.

First make sure you have HPLIP install by going to a terminal and issuing this command ```
sudo apt-get install hplip
```
next go to a web browser and type this in the address bar ```
http://localhost:631
```
this will bring you to the cups setup screen follow the instructions to add printer. 

good luck :)

---

