---
title: "Epson SX405 not working in Hardy"
date: 2008-08-20
forum: Hardware
---

### Post by stardustdk on 2008-08-20
Hej All.

A friend have just bought a Epson Stylus SX405 to work with Ubuntu Hardy.

Anyone with a idea if and how I can get the printer and Ubuntu to work?

Best regards

Stardustdk

---

### Post by kggra on 2008-11-05
I also have the same problem with my new sx405 but have got printing working by pretending its an Epson CX3650. (Ubuntu recognises the printer as an SX405 ok, just change the "make and model" to Epson CX3650).

---

### Post by rocoat82 on 2009-02-22
> **kggra said:**
> I also have the same problem with my new sx405 but have got printing working by pretending its an Epson CX3650. (Ubuntu recognises the printer as an SX405 ok, just change the "make and model" to Epson CX3650).

Hello guise.
I want inform you that on [http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_SX405]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_SX405") are present driver for EPSON SX405. On Avasys site, i've also found driver for scanner (64bit version in my case).

Bye

---

### Post by mdrenwick on 2009-05-05
Just managed to get the Epson Stylus SX 405 working.

I'm sharing the printer with a (cough) Win2K machine, two Ubuntu laptops and a Ubuntu desktop, using the wired ethernet Edimax print server that comes with the Epson.

I've installed the Epson on the Ubuntu boxes as a LPD printer as per the user manual I found on the Edimax website.

Steps:
1) I found the DHCP'd ip address of the Edimax by interogating my broadband router.
   (e.g. firefox to 192.168.0.1)  

2) Using firefox I browsed to the Edimax ip address [username=admin, password=1234]

3) I then set the ip setting to static values 
   (eg: ip=192.168.0.70, subnet 255.255.255.0, gateway=192.168.0.1)

4) Then add new printer:
   System -> Administration -> Printing... New
   Network Printer -> LPD/LPR Printer
   (E.g. Host=192.168.0.70, Queue=p1)
   Forward...

5) And select the Epson SX405 from the list.

Ta da

---

