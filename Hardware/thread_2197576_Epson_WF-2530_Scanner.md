---
title: "Epson WF-2530 Scanner"
date: 2014-01-04
forum: Hardware
---

### Post by granul on 2014-01-04
Hi!

I installed a Epson printer WF-2530 wifi on Ubuntu 13.04, the printer works but not the scanner, I always get error message, I hear the scanner, seems to work but after a few second I get an communication error? Any Idea?

---

### Post by specialwizard17 on 2014-01-06
Hi

Having looked on the SANE project website, the WF-2530 scanner is not (yet) supported.

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

I also own a WF-2530 scanner and encounter similar problems. The problem occurs both with the Flatbed and ADF choices. When I attempt to scan a document, the scanner commences the scanning operation and then hangs before completing the scanning operation. I then need to switch off and restart the WF-2530 machine itself while Ubuntu returns the error:

"Failed to start scanner: Error during device I/O"

If there is a workaround around this, then any help by the community would be very much appreciated.

---

### Post by Redsandro on 2014-01-30
I just bought this Epson WF-2530 in a discount, specifically for scanning a bunch of stuff using the automatic document feed.
Little did I know that it wasn't supported in Linux yet!

Any workaround would be greatly appreciated.

BTW, I don't get the partial scan movement with communication error. Ubuntu simply says: *"No scanners found."*

---

### Post by Redsandro on 2014-01-30
On the other hand, you can search for 2530 here to find a bunch of scanner related drivers:
[http://download.ebz.epson.net/dsc/search/01/search/](http://download.ebz.epson.net/dsc/search/01/search/)

I installed **iscan-data_1.26.0-1_all.deb** and **iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb**.
They claim to support this scanner on Linux, but I am not having any luck yet.

---

### Post by Redsandro on 2014-01-30
After installing those two packages, rebooting (while printer connected and turned on) makes the scanner work in xsane! Yay!

---

### Post by specialwizard17 on 2014-02-01
Hi Redsandro

Thanks for the information. I got my printer also working in Ubuntu though with the USB connection. The truth is I hadn't tried using the USB connection first time round, as I wanted to get it working over the WiFi network. Unfortunately the scanner still doesn't operate correctly when controlling it over the network but works great (flatbed and ADF) when using the USB connection.

Cheers for the info.

---

### Post by theGiallo on 2014-07-19
Hi, I'm using debian, and I've found that in the file /etc/sane.d/epkowa.conf  there is no net configuration by default, so I added my scanner IP and now the  scanner is seen. (epkowa must be added to /etc/sane.d/dll.conf )
[ I have installed all the epson iscan packages]

Also to use iscan plugin in GIMP you have to link the iscan bin into the GIMP plug-ins dir -> [http://slackbuilds.org/repository/12.2/system/iscan/](http://slackbuilds.org/repository/12.2/system/iscan/)

---

### Post by granul on 2014-07-20
> **theGiallo said:**
> Hi, I'm using debian, and I've found that in the file /etc/sane.d/epkowa.conf  there is no net configuration by default, so I added my scanner IP and now the  scanner is seen. (epkowa must be added to /etc/sane.d/dll.conf )
[ I have installed all the epson iscan packages]

Also to use iscan plugin in GIMP you have to link the iscan bin into the GIMP plug-ins dir -> [http://slackbuilds.org/repository/12.2/system/iscan/](http://slackbuilds.org/repository/12.2/system/iscan/)

I dont see a file epkowa.conf, there is epson.conf.

---

### Post by theGiallo on 2014-07-20
> **granul said:**
> I dont see a file epkowa.conf, there is epson.conf.

Hmm...

I have:
[LIST=1]
[*]libsane version 1.0.24-1.1+b1
[*]iscan version 2.29.3-1~usb0.1.ltdl7
[*]iscan-data version 1.27.0-1
[*]iscan-network-nt version 1.1.1-1
[/LIST]

Try to run *scanimage -L* and look for net configuration in */etc/sane.d/*{*epson2.conf, epson.conf*} and for {*epson2, epson*} in */etc/sane.d/dll.conf* maybe they will work.

You can look for a scanner with a defined protocol, for example *scanimage epkowa:net:192.168.1.33*

---

### Post by granul on 2014-07-20
Thank you for the help

Here is what I get with scanimage -L:
device `epson2:net:192.168.1.18' is a Epson PID 08A6 flatbed scanner

So I change the address in epson2.conf but I still get error that says impossible to scan, the communication with the scanner seems to be there but does not scan.

---

### Post by theGiallo on 2014-07-20
Hmm, I get [I]is a Epson WF-2520/2530/2540 Series flatbed scanner
[/I]Have you installed the debs from Epson website (the ones linked by Redsandro)?

---

### Post by granul on 2014-07-20
> **theGiallo said:**
> Hmm, I get [I]is a Epson WF-2520/2530/2540 Series flatbed scanner
[/I]Have you installed the debs from Epson website (the ones linked by Redsandro)?

I installed epson-inkjet-printer-201211w_1.0.0-1lsb3.2_amd64.deb and iscan_2.29.3-1~usb0.1.ltdl3_amd64.deb, The printer is working but not the scanner

---

### Post by theGiallo on 2014-07-31
> **Redsandro said:**
> On the other hand, you can search for 2530 here to find a bunch of scanner related drivers: [http://download.ebz.epson.net/dsc/search/01/search/](http://download.ebz.epson.net/dsc/search/01/search/)  I installed **iscan-data_1.26.0-1_all.deb** and **iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb**. They claim to support this scanner on Linux, but I am not having any luck yet.  > **granul said:**
> I installed epson-inkjet-printer-201211w_1.0.0-1lsb3.2_amd64.deb and iscan_2.29.3-1~usb0.1.ltdl3_amd64.deb, The printer is working but not the scanner  I have these installed:  iscan-data_1.27.0-1_all.deb iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb iscan-network-nt_1.1.1-1_amd64.deb

---

