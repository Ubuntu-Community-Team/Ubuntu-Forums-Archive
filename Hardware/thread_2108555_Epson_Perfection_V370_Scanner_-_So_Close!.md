---
title: "Epson Perfection V370 Scanner - So Close!"
date: 2013-01-24
forum: Hardware
---

### Post by Gatch on 2013-01-24
Bought this scanner recently and thought it would run on 12.04. No dice, should have checked the hardware list first.

Loaded driver from Epson; epkowa backend and xsane. Followed some great directions here on the forum. Got xsane to recognize it but when I hit the "scan" button this error message appears:

"Failed to start scanner: invalid argument" 

Any ideas? Been fighting this for a couple days.

---

### Post by typhoon_tip on 2013-01-25
Have you tried to use Simple Scan default scan program in Ubuntu instead ? Worked all the times for me without much hassles !

---

### Post by Gatch on 2013-01-25
Yeah. Tried that too. Gave a similar error response.

---

### Post by pdc on 2013-01-27
I guess if we backtrack and check what you did; (as you spare us the details!!)

......perhaps we check what iscan packages you have installed ..

...if you copy and paste this command into a terminal ..

....and copy and paste back the result

> [COLOR="Red"]sudo dpkg -l | grep iscan[/COLOR]

.. for the Epson driver you went here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21462&DSCCHK=c30d90015ed5b1fc7bdce14ddffdc4e65a538440](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21462&DSCCHK=c30d90015ed5b1fc7bdce14ddffdc4e65a538440)

and downloaded then installed [COLOR="Blue"]FIRST[/COLOR] the data package

[COLOR="SeaGreen"]iscan-data_1.21.0-1_all.deb[/COLOR]

and then downloaded & installed the [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.[COLOR="Magenta"]ltdl7[/COLOR]_i386.deb[/COLOR]

.........as you don't tell us and I assume you are on 32bit 12.04? 

and the [COLOR="Magenta"]ltd7[/COLOR] is for recent kernels .........

and then added the [COLOR="SeaGreen"]iscan-plugin-perfection-v370_1.0.0-2_i386.deb[/COLOR] from here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20224&DSCCHK=0b6f1fab069ceaaa5a69b7be6d1439f94ab5276a](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20224&DSCCHK=0b6f1fab069ceaaa5a69b7be6d1439f94ab5276a)

........Epson would sort of expect your scanner to work after doing that

---

### Post by Gatch on 2013-01-27
Thanks PDC -
Yes it is 32bit 12.04

The results for iscan are:
> ii  iscan                                  2.29.1-5~usb0.1.ltdl7                   simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                             1.21.0-1                                Image Scan! for Linux data files
ii  iscan-plugin-perfection-v370           1.0.0-3                                 Plugin for the GT-F740/S640 and Perfection V37/V370 Photo


I downloaded the plug-in first, then the data file. Does that make a difference?

After your post I downloaded an installed the
> iscan_2.29.1-5~usb0.1.ltdl7_i386.deb

The error message for iscan is: > Could not send command to scanner. Check the scanner's status.

Xsane says it is busy. 

Any thoughts?

---

### Post by pdc on 2013-01-27
I googled on 


> [COLOR="Magenta"]Could not send command to scanner. Check the scanner's status.[/COLOR] 

....... and one gets many answers, all focused on epkowa being present in a key file ...........

and I got this Epson guide support.epson.ru/upload/library_file/11/scanner_linux.pdf

if you copy and paste

> [COLOR="Red"]gksudo gedit /etc/sane.d/dll.conf[/COLOR]

.....that opens up the text editor with write properties; (usually is read-only)

and paste the word

> [COLOR="Blue"]epkowa[/COLOR] into the list; (if not already there);

Save: Close

restart system: any joy?

---

### Post by Gatch on 2013-01-27
This seems strange. I ran [COLOR="Red"]sane-find-scanner[/COLOR] in the terminal and got this result:
> found USB scanner (vendor=0x04b8 [EPSON], product=0x014a [EPSON Perfection V37/V370]) at libusb:001:005
found USB scanner (vendor=0x1737, product=0x0078) at libusb:001:003

It looks like it lists two scanners but only one is connected. Weird

---

### Post by Gatch on 2013-01-27
Added [COLOR="Red"]epkowa[/COLOR] to the /etc/sane.d/dll.conf file. Didn't make a difference.

---

### Post by amidsin on 2013-03-04
I have also faced the problem of connecting Epson Perfection V37 scanner to Ubuntu (12.04, x64). It worked just fine for me based on directions from pdc (post #4).

It looks like URLs on the Epson download side are dynamic so that didn't work as is. I used following URL to find necessary packages:
[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)
Searched for "Perfection V37", selected link package first, installed following packages:
iscan-data_1.22.0-1_all.deb
iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
Then selected link for iscan plugin package, installed following package:
iscan-plugin-perfection-v370_1.0.0-2_amd64.deb

Right after that it still didn't work, but after reconnecting scanner, I was able to use Simple Scan (simple-scan).

Thank you for help.

---

### Post by rodericj on 2013-09-14
I have just replaced a broken Epson V200 with a V370 and have it installed on two machines running 13.04 and 13.10. It works perfectly with simple scan BUT it will not work if plugged into a USB3 port - it needs to be plugged into a USB 2 port. I hope this helps.

---

### Post by craig.mackey on 2013-12-02
I have just upgraded to Ubuntu 13.10 desktop 32bit, purchased an Epson V370 for my Win 7 PC and wanted to set it up on  ubuntu so found this [post]("http://www.linux-hardware-guide.com/2013-06-16-epson-perfection-v370-color-photo-scanner"), downloaded and installed the *.deb packages, from [here]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") via cli, in the order below and it worked no problems.iscan
iscan-data
iscan-plugin-perfection-v370

hope this helps.

---

### Post by davethesteam on 2014-08-18
Just got me new Epson v370 photo.

OK, so I have just used the basic function so far, but joy of joys - it works!!!.

3 downloads were needed from the Epson web site (oh, so slow!!) which is accessed through the main page / support then choose your product and OS:
1st was from 'all debian'
2nd was by choosing the correct debian package (I have 14.04 LTS 64 bit) thus the one calling for 'Ubuntu 8.10 and later and the 64 bit version showing something like 'libits7')
3rd was another packege for the Epson scanning function (Image Scan for linux)

All installed fine through the installer

Once all down loaded, scanner was switched on, system re booted and Hey presto!!

---

### Post by pdc on 2014-08-18
well done Dave;

so you would have installed the **DATA** package first ........... [COLOR="#008000"]iscan-data_1.29.0-2_all.deb[/COLOR]

then the [COLOR="#008000"]iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb[/COLOR] for 64bit

then [COLOR="#008000"]iscan-plugin-perfection-v370_1.0.0-2_amd64.deb[/COLOR]	..................the network plugin package

---

### Post by davethesteam on 2014-08-19
Hi pdc
Yes that is correct because installation manager would not install by installing the second one first.
Still - hey ho - it worked!!

---

