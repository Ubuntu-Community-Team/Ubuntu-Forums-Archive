---
title: "Printers - Print with reverse page order by default"
date: 2014-05-02
forum: Hardware
---

### Post by armithaeus on 2014-05-02
Hello,

I am new to Kubuntu 14.04 and wanted to set up my printer EPSON Epson Stylus Office BX935FWD which is connected to my network.
System Settings -> Printers -> Add Printer shows 2 Discovered printers for the BX935FWD.
1 with AppSocket/JetDirect network printer via DNS-SD and another with the options to enter an address and a queue.
I selected the Appsocket/JetDirect one and choose Epson Workforce 845 as driver since my model wasn't supported directly.
I tested it later with a ppd driver downloaded from epson for my model.

Both drivers print alright, but I have with both the same issue:
The default page order is incorrect. I need it reversed.
I tried the suggestions here: [http://ubuntuforums.org/showthread.php?t=1320518](http://ubuntuforums.org/showthread.php?t=1320518)

> lpoptions -o outputorder=reverse

and adding

> *DefaultOutputOrder: Reverse

to the ppd. I also checked out the web interface, but there was no option to reverse it there.

If I select "reverse" in the system print dialog, I get the correct output, but I want the correct order by default.

Any input on how I can manage to reverse it?
(I am new to Kubuntu, so please guide me in Noob-understandable steps.)

Thanks a lot
armithaeus

---

### Post by pdc on 2014-05-02
If you did want to track down the driver that Epson releases for your device BX935FWD , go here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16841&DSCCHK=14843664b2eb7961bfb698ac6c420ec3d58bd0cb](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16841&DSCCHK=14843664b2eb7961bfb698ac6c420ec3d58bd0cb)

for 32bit: epson-inkjet-printer-201107w_1.0.0-1lsb3.2_i386.deb

for 64bit: epson-inkjet-printer-201107w_1.0.0-1lsb3.2_amd64.deb

when you click to download, your system should offer to "open with gdebi installer": that would be a direct way of installing .........

---

### Post by armithaeus on 2014-05-02
> **pdc said:**
> If you did want to track down the driver that Epson releases for your device BX935FWD , go here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16841&DSCCHK=14843664b2eb7961bfb698ac6c420ec3d58bd0cb](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16841&DSCCHK=14843664b2eb7961bfb698ac6c420ec3d58bd0cb)

for 32bit: epson-inkjet-printer-201107w_1.0.0-1lsb3.2_i386.deb

for 64bit: epson-inkjet-printer-201107w_1.0.0-1lsb3.2_amd64.deb

when you click to download, your system should offer to "open with gdebi installer": that would be a direct way of installing .........
my current ppd comes from that deb which I installed after the first tests with the workforce driver. but it doesn't fix the issues with the reverse page order.

---

