---
title: "hp p1102w print problems"
date: 2011-08-08
forum: Hardware
---

### Post by hubiedo on 2011-08-08
am on ubunto 10.04 lts. i have a hp p1102w printer w/ the latest hplip setup on it 3.11.7 and it works for open word documents, etc. this is installed as a usb printer

it will not print from kmail, evolution emails etc., does print from the internet etc. it does try to print from kmail but is just garbage, evolution no print. it appears it has do do with pdf files. using the debug i got message /usr/lib/cups/filter/pdftraster failed. 

this apparently has to do with ghostscript. should i reinstall ghostscript also?

further research indicates a patch. should i install it? if so how do you install after downloadn the patch? 

another problem is setting up the network printer via wifi. once the printer is set to broadcast it gives me a SSID and ip address. once i find it on my network and change it my SSID what do i do with the ip address? change it an address on my network? 

sample printer SSID=XXXX IP=167.220.15.197 my network is johnnet w/ network id 192.168.2.1 should i give it a new ip address on my network? can someone give me some idea of how to do the actual setup. i have gotten it this far but not sure how to set the ip addresses/gateway etc.

what am i doing wrong? can anyone point me the right direction or have any similar experience.

---

### Post by Barbara0415715 on 2011-08-21
I had problems with the HP LaserJet P1102w and Ubuntu Lucid (10.04), but I solved it.
I use the USB-connection, so I haven't tried it with the WiFi yet.

The P1102w uses the driver foo2zjs, but you need a version newer than 2010-05-28. 
The version in Lucid (10.04) is too old, but the one in Maverick (10.10) works fine. 
Luckily you can install the package from Maverick in Lucid without dependency problems.

Instructions:

- Go to [http://packages.ubuntu.com/maverick/foo2zjs](http://packages.ubuntu.com/maverick/foo2zjs)

- Download the right package. Don't know if you need amd64 or i386? Type in a terminal: 
```
dpkg --print-architecture
```
- Install gdebi if you don't have it already: 
```
sudo aptitude install gdebi
```
- Install the printer driver: 
```
gdebi foo2zjs_*.deb
```

If you already have an older version of foo2zjs, you can replace the last two steps with (I didn't test this):
```
dpkg -i foo2zjs_*.deb
```

---

