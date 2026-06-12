---
title: "Canon mx360 printer driver with ubuntu 14.04.1"
date: 2014-09-13
forum: Hardware
---

### Post by holliswuhollis on 2014-09-13
Hi,

I have installed ubuntu gnome 14.04.1 recently. However, I found out that the driver of my printer, canon mx 366, can't detect my printer.
It is known that this printer uses the Canon MX 360 driver.
Back to ubuntu 12.04, I can install the driver and use it properly. (I have left Ubuntu since then)
I have googled about this problem and found some solution. Including manually install libtiff4 (seems that ubuntu stop supporting libtiff4 and use libtiff5 instead. However, Canon didn't update the driver for this).
Here's are some result of google:
    [http://goo.gl/eO3eoc](http://goo.gl/eO3eoc)
    [http://goo.gl/3LVqEC](http://goo.gl/3LVqEC)
Some of the reader reported that they can use the meathod properly under Ubuntu 14.04. But I am still facing the problem.
I am sure that the USB wire is connected(I can use the printer properly in Windows). The power is also on.

Thanks for readting this. If I have made any grammer mistake or need more information, please leave a comment under this.
Thank you. :)

---

### Post by pdc on 2014-09-13
Hi Hollis;

I think you are saying you want to get the printer working; so on that assumption, I am listing instructions below; I hope I have read your post correctly

__________________________

[SIZE=3]**Libtiff 4**[/SIZE]

yes, for your device, Canon supply the version 3.5 series printer driver; it needs libtiff4; from version 4, the printer driver does not require libtiff4;

to get libtiff 4 installed, can I point you to the debian repository? [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/)

go down the list.............14 or 18.........and choose the 64bit or 32bit version..............click to install;

_________________________

**Canon driver **

If you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100329501.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100329501.html?r=s&q=) and click to download and SAVE: you will get [COLOR="#008000"]cnijfilter-mx360series-3.50-1-deb.tar.gz
[/COLOR]
If you open a terminal; paste each command below; **line by line** ............hit ENTER after each paste ..........

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mx360series-3.50-1-deb.tar.gz
cd cnijfilter-mx360series-3.50-1-deb
./install.sh[/COLOR]

that starts the install script. 

_______________

---

### Post by holliswuhollis on 2014-09-14
> **pdc said:**
> Hi Hollis;

I think you are saying you want to get the printer working; so on that assumption, I am listing instructions below; I hope I have read your post correctly

__________________________

[SIZE=3]**Libtiff 4**[/SIZE]

yes, for your device, Canon supply the version 3.5 series printer driver; it needs libtiff4; from version 4, the printer driver does not require libtiff4;

to get libtiff 4 installed, can I point you to the debian repository? [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/)

go down the list.............14 or 18.........and choose the 64bit or 32bit version..............click to install;

_________________________

**Canon driver **

If you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100329501.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100329501.html?r=s&q=) and click to download and SAVE: you will get [COLOR=#008000]cnijfilter-mx360series-3.50-1-deb.tar.gz
[/COLOR]
If you open a terminal; paste each command below; **line by line** ............hit ENTER after each paste ..........

[COLOR=#FF0000]cd Downloads
tar -zxvf cnijfilter-mx360series-3.50-1-deb.tar.gz
cd cnijfilter-mx360series-3.50-1-deb
./install.sh[/COLOR]

that starts the install script. 

_______________


Thank you.

That is the problem I am facing. I have run the install script and it said it can't find the printer

This is the output of the script:

&#9654; ./install.sh 
[sudo] password for h: 
==================================================

Canon Inkjet Printer Driver Ver.3.50-1 for Linux
Copyright CANON INC. 2001-2011
All Rights Reserved.

==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.50-1_amd64.deb
dpkg: &#19981;&#26371;&#23559; cnijfilter-common &#24478; 3.90-76~ubuntu14.04.1 &#38477;&#32026;&#21040; 3.50-1&#65292;&#30053;&#36942;                              (translate: dpkg: will not downgrade cnijfilter-common, from 3.90-76~ubuntu14.04.1 to 3.50-1, skipping)
Command executed = sudo dpkg -iG ./packages/cnijfilter-mx360series_3.50-1_amd64.deb
dpkg: &#19981;&#26371;&#23559; cnijfilter-mx360series &#24478; 3.90-76~ubuntu14.04.1 &#38477;&#32026;&#21040; 3.50-1&#65292;&#30053;&#36942;                        (translate: dpkg: will not downgrade cnijfilter-mx360series, from 3.90-76~ubuntu14.04.1 to 3.50-1, skipping)
status: Unknown job: cups

#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

Searching for printers...


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Could not detect the target printer.
-----------------------------------------------------------
Currently selected:[0] Update
Enter the value. [0]


I have turned my printer on. But the script still can't find the printer.

---

### Post by pdc on 2014-09-14
> I have run the install script and it said it can't find the printer

OK: tell us if it is connected by usb? if so, 

1) can you paste this command into a terminal > [COLOR="#FF0000"]lsusb[/COLOR]

also: 

2) can you paste this command > [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR]

____________________________________________

so from the install script, it seems you have already installed Canon drivers ..........

3) can you paste this command > dpkg -l | grep cnijfilter

___________________________________________

can you paste the results of the inquiries back here please:

---

### Post by holliswuhollis on 2014-09-14
Yes, it is connected by USB.

The output of "lsusb"
> 
Bus 002 Device 004: ID 093a:2521 Pixart Imaging, Inc. 
Bus 002 Device 003: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04a9:174d Canon, Inc. MX360 ser
Bus 003 Device 002: ID 2109:3431  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



The output of "[COLOR=#FF0000][/COLOR]/usr/sbin/lpinfo -v"[COLOR=#FF0000]
[/COLOR]> 
network lpd
network https
network ipp
network ipp14
network ipps
network http
network socket
direct usb://Canon/MX360%20series?serial=300799&interface=1
direct hp
direct usb://Canon/MX360%20series%20FAX?serial=300799&interface=2
direct cnijusb:/dev/usb/lp0
direct cnijusb:/dev/usb/lp1
network smb
direct hpfax
[COLOR=#FF0000]

[/COLOR]Output of [COLOR=#FF0000][/COLOR]"dpkg -l | grep cnijfilter"[COLOR=#FF0000]
[/COLOR]> 
ii  cnijfilter-common                           3.90-76~ubuntu14.04.1                 i386         IJ Printer Driver for Linux.
rc  cnijfilter-common-64                        3.90-76~ubuntu14.04.1                 amd64        IJ Printer Driver for Linux.
ii  cnijfilter-mx360series                      3.90-76~ubuntu14.04.1                 i386         IJ Printer Driver for Linux.
rc  cnijfilter-mx360series-64                   3.90-76~ubuntu14.04.1                 amd64        IJ Printer Driver for Linux.

[COLOR=#FF0000]
[/COLOR]

---

### Post by pdc on 2014-09-14
> Could not detect the target printer

.............I don't know why this is happening

I wonder if you paste > [COLOR="#FF0000"]system-config-printer[/COLOR] into a terminal; and from the dialogue box that opens; can you "Add a new printer" that way...........searching for your MX360 ...............

---

### Post by holliswuhollis on 2014-09-15
Hi,

I have done it. System finally found my printer.

Don't know why I can suddenly found it. Mabye I have to reboot or turn my printer on before my computer is on.

Thanks for helping me.

---

### Post by pdc on 2014-09-15
> I have done it. System finally found my printer.

well done; enjoy

Canon supply [COLOR="#0000FF"]ScanGearMP[/COLOR] to run the scanner side of your device; it installs the same way the printer driver does: let us know if you want instructions;

it runs from a terminal with the command > [COLOR="#FF0000"]scangearmp[/COLOR] and one sets up a launcher to "launch" it for repeated use 

(You can use thread tools to edit your post to SOLVED)

---

