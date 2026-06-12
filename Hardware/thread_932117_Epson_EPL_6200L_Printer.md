---
title: "Epson EPL 6200L Printer"
date: 2008-09-28
forum: Hardware
---

### Post by bidger on 2008-09-28
I am trying to install an Epson EPL 6200 Laser Printer on my Xubuntu machine ... USB connection and the OS seems to see the printer but nothing prints - no documents, no test pages ... nothing nada nil.

Any help greatly appreciated.

---

### Post by bidger on 2008-09-28
I have tried the following from another topic (archived):

> Hi, I finally managed to get the printer working in
Hardy, i suspect the same solution might apply on
Gutsy also.

Download epsoneplijs-0.4.0.tgz;
[http://sourceforge.net/projects/epsonepl/](http://sourceforge.net/projects/epsonepl/)

Compile and install:
tar zxvf epsoneplijs-0.4.0.tgz
cd epsoneplijs-0.4.0
[B]./configure --prefix=/usr
[/B]./make
sudo make install

Then install the printer using this PPD file:
[http://www.nemesys.fi/tiedostot/ubun...200L-Hardy.ppd](http://www.nemesys.fi/tiedostot/ubun...200L-Hardy.ppd)

There u go!

I am using the latest tarball (0.4.1) and amended the commands appropriately, but it is not helping - when I get to the bolded line (./configure) I get the following response:

> checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Any ideas?  Am I flogging a dead printer here?:confused:

Bidger @ Darwin

---

### Post by bidger on 2008-09-30
Bump.

---

### Post by Sef on 2008-09-30
Paste the results from this code:

> lsusb

---

### Post by bidger on 2008-10-02
> **Sef said:**
> Paste the results from this code:

lsusb

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 0bc2:0503 Seagate RSS LLC 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 079: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000


So I guess it sees the printer, but when I send things to it nothing appears.

---

### Post by bidger on 2008-10-11
Bump.

---

