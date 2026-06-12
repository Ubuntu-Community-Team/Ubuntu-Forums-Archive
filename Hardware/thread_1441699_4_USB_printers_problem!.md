---
title: "4 USB printers problem!"
date: 2010-03-29
forum: Hardware
---

### Post by daniel-strae on 2010-03-29
Hi guys, forst of all sorry if my english is not perfect :D

Im started using ubuntu two months ago, and now im trying to switch my office's pc to ubuntu too.

Everythings works perfectly, the only problem i have is with the printers: i have 4 Epson usb printers, 2 R285 and 2 P50 linked to my pc.

Those printers works, but seem like ubuntu consider them as 2;

Printer A: Epson P50;
Printer B: Epson P50;
Printer C: Epson R285;
Printer D: Epson R285;

So, the first P50 i switch on is the one ubuntu see: if i switch on the A printer, ubuntu will print with it and completely ignore the printer B and viceversa, the same happen for the C and D printers.

I saw in system->Print->Printer A->Properties that the URI of the printers are the same for the model, so printers A and B have that URI:
usb://EPSON/Stylus%20Photo%20P50
C and D:
usb://EPSON/Stylus%20Photo%20R285

and i think that this is the problem.

There is a way to 'map' the printers, for example 'Printer A from the USB port #1, Printer B from USB #2, etc...'?

---

### Post by daniel-strae on 2010-03-29
This is the output of my `sudo printconf`:

```

 * Reloading Common Unix Printing System: cupsd
   ...done.
Printer on usb:/dev/usb/lp0 was detected by Debian using the ad-hoc method.  Please submit the following information to
foomatic-db@packages.debian.org:
<autodetect>
  <usb>
    <commandset>ESCPL2,BDC,D4,D4PX</commandset>
    <description>EPSON Stylus Photo R285</description>
    <manufacturer>EPSON</manufacturer>
    <model>Stylus Photo R285</model>
  </usb>
</autodetect>

Epson Stylus Photo R285 on USB Printer #1 is not currently supported by Debian.

Printer on usb:/dev/usb/lp1 was detected by Debian using the ad-hoc method.  Please submit the following information to
foomatic-db@packages.debian.org:
<autodetect>
  <usb>
    <commandset>ESCPL2,BDC,D4,D4PX</commandset>
    <description>EPSON Stylus Photo R285</description>
    <manufacturer>EPSON</manufacturer>
    <model>Stylus Photo R285</model>
  </usb>
</autodetect>

Epson Stylus Photo R285 on USB Printer #2 is not currently supported by Debian.

Printer on usb:/dev/usb/lp2 was not automatically configurable by Debian.  Please submit the following information to
foomatic-db@packages.debian.org:
<autodetect>
  <usb>
    <commandset>ESCPL2,BDC,D4,D4PX</commandset>
    <description>EPSON Epson Stylus Photo P50</description>
    <manufacturer>EPSON</manufacturer>
    <model>Epson Stylus Photo P50</model>
  </usb>
</autodetect>

Printer on usb:/dev/usb/lp3 was not automatically configurable by Debian.  Please submit the following information to
foomatic-db@packages.debian.org:
<autodetect>
  <usb>
    <commandset>ESCPL2,BDC,D4,D4PX</commandset>
    <description>EPSON Epson Stylus Photo P50</description>
    <manufacturer>EPSON</manufacturer>
    <model>Epson Stylus Photo P50</model>
  </usb>
</autodetect>

If printconf was unable to install all of your printers, please visit http://www.linuxprinting.org/ for printer information
and support from fellow users.

```

I tryed to put usb:/dev/usb/lp$X in the URI parameters of the printers, but it doesnt work!

---

### Post by Fafler on 2010-03-29
I think it could be fixed with udev. It's been a while, so i can't exactly remember what to do, but look at the info available to udev and look for a serial number or something else unique to each printer and use it to map the printer to a device name of your choice.

---

### Post by wyliecoyoteuk on 2010-03-29
Looks like the 285s are not being recognised as supported.

I would try opening CUPS directly and try reconfiguring, perhaps deleting and then reading the printers and selecting the drivers would help.

CUPS 

[http://localhost:631](http://localhost:631)


My URIs for  USB printers:

hp:/usb/Deskjet_F2200_series?serial=CN89O4Q0430534 
hp:/usb/deskjet_3420?serial=HU28T3Q2M41J 

So  maybe you can add it thus:

usb://EPSON/Stylus%20Photo%20P50?serial=<serial number of your printer>

---

### Post by daniel-strae on 2010-03-29
> **wyliecoyoteuk said:**
> Looks like the 285s are not being recognised as supported.

I would try opening CUPS directly and try reconfiguring, perhaps deleting and then reading the printers and selecting the drivers would help.

CUPS 

[http://localhost:631](http://localhost:631)


My URIs for  USB printers:

hp:/usb/Deskjet_F2200_series?serial=CN89O4Q0430534 
hp:/usb/deskjet_3420?serial=HU28T3Q2M41J 

So  maybe you can add it thus:

usb://EPSON/Stylus%20Photo%20P50?serial=<serial number of your printer>

Thanks, i'll try to add the serial number..

@Fafler: i'll give a read to udev

The funny things is that via CUPS i can see two others R285 linked to an apple powermac, and i recognize them individually.. i suppose its a usb problem, and maybe i'll solve them easly if i put my 4 printers in the network.. but my pronters doesnt have the lan plugin -.-

---

### Post by daniel-strae on 2010-03-30
The ?serial= trick didnt work :sad:

And im getting crazy trying to map the printers with udev, googled a lot, but didnt find anythings for usb printers (but many tutorial for usb scanners -.-)

---

### Post by Fafler on 2010-03-30
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

I don't have any USB printers, so i can't be more specific, but feel free to ask any questions.

---

### Post by Bungler on 2010-03-30
Have you tried to plug 1 of them in at the back usb connector and 1 in the front one, or on a seperate USB card?
I have to admit it is a guess, but I tought the usb ports are grouped on the motherboard and if connect them on different groups might make a difference

---

