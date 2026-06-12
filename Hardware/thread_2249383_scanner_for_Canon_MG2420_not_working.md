---
title: "scanner for Canon MG2420 not working"
date: 2014-10-21
forum: Hardware
---

### Post by bandito40 on 2014-10-21
Just bought a Canon MG2420 all-in-one printer.  Have Ubuntu 14.04 installed. Detects printer but scanner is not detected.  Can anyone help?

---

### Post by bandito40 on 2014-10-22
I found the driver on the Cannon website. [http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/MG2440.aspx?type=download&language=EN&os=Linux]("http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/MG2440.aspx?type=download&language=EN&os=Linux")

When I extract from the tar.gz file there is no .deb file. Instead there is folder with an install.sh file and two other folders.  I have run the install.sh file and it appears to be installing the driver but eventually crashes with the following error:


Command executed = sudo /usr/sbin/lpadmin -p printer1 -m canonmg2400.ppd -v cnijbe://Canon/?port=usb&serial=D277CD -E
lpadmin: Unable to copy PPD file.
The printer registration has not been completed.
Register the printer manually by using the lpadmin command.


I run locate and found a ppd file that appears to be a MG2400 ppd file.
I then tried running the lpadmin with the absolute path this ppd file but that gives me this error:

lpadmin: Unable to copy PPD file.
-E: command not found
[1]+  Exit 1                  sudo /usr/sbin/lpadmin -p mg -m /etc/cups/ppd/Canon_MG2400_series.ppd -v cnijbe://Canon/?port=usb

Anyone know what to do here?

---

### Post by pdc on 2014-10-24
I start at the Canon Asia website [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

for the 2400 series devices, I would end up here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100551701.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100551701.html) and I would click to DOWNLOAD and I would select SAVE and I would get [COLOR="#006400"]scangearmp-mg2400series-2.20-1-deb.tar.gz[/COLOR]

I would open a terminal and paste in the commands that are below; line by line; hitting the ENTER key after each paste ................

[COLOR="#FF0000"]cd Downloads
tar-zxvf scangearmp-mg2400series-2.20-1-deb.tar.gz
cd scangearmp-mg2400series-2.20-1-deb
./install.sh[/COLOR]

and that should install ScanGearMP that is the programme Canon supply to drive their scanner; 

and crucially to run it, one would type > [COLOR="#FF0000"]scangearmp[/COLOR] in a terminal and then set up a launcher to ............... launch it each time in the future ...............

---

