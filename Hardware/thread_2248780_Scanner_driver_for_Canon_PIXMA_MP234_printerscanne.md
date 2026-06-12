---
title: "Scanner driver for Canon PIXMA MP234 printer/scanner"
date: 2014-10-17
forum: Hardware
---

### Post by huttondb1 on 2014-10-17
Using Ubuntu 14.04LTS in the Philippines:  Printing works fine but the scanner is not.  I have found no way to access it,  I downloaded and tried SANE software but it did not work.  I could not find my printer on the Canon website even though I bought it less than a year ago.  I can not download a driver using Software Update because I have no Athenication key.  I see keys listed under the athenication tab of Software Update along with a date.  I have been unsusseful entering any of these.  I can not believe there are no Linux drivers out there but I am  stumpted as how to download and install a driver.  I saw no thread of this problem but do not think it is that uneque.

---

### Post by pdc on 2014-10-17
Canon provide a linux scanner driver for all their MF devices; the programme is called [COLOR="#0000FF"][SIZE=3]**ScanGearMP**[/SIZE][/COLOR] and a particular variant is made available for each device

if you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100469501.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100469501.html?r=s&q=) and click to download and SAVE you will be getting [COLOR="#008000"]scangearmp-mp230series-2.00-1-deb.tar.gz[/COLOR]

if you can open a terminal; and copy and paste each command that I give below; into the terminal; and hit the ENTER key after each paste; it will install the driver for you

[COLOR="#FF0000"]cd Downloads
tar -zxvf scangearmp-mp230series-2.00-1-deb.tar.gz
cd scangearmp-mp230series-2.00-1-deb
./install.sh[/COLOR]

and that will ask you for your sudo password. 

To run [COLOR="#0000FF"][SIZE=3]**ScanGearMP**[/SIZE][/COLOR], type or paste into the terminal > [COLOR="#FF0000"]scangearmp[/COLOR] and that will run the programme

then you need to set up a LAUNCHER; many will argue the best way to do it: here is a link [http://www.youtube.com/watch?v=Q-Cl7HRsEUU](http://www.youtube.com/watch?v=Q-Cl7HRsEUU) that has one person's method

______________________________________________________

NOTE: [COLOR="#0000FF"][SIZE=3]**ScanGearMP**[/SIZE][/COLOR] has nothing to do with simple scan; or xsane; as they are from the open-source sane work; 

____________________________________________________--

>  I could not find my printer on the Canon website

I was sorry to hear this; here is the link I use: [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

 see if you can find your way to the link I have given you; 

______________________________________________________

actually I then looked on your Phillipines website

[http://www.canon.com.ph/PRODUCTS/PRINTERSFACSIMILES.aspx](http://www.canon.com.ph/PRODUCTS/PRINTERSFACSIMILES.aspx)

[http://www.canon.com.ph/products/PRODUCTS/PRINTERSFACSIMILES/INKJET/ALLINONEINKJET.aspx](http://www.canon.com.ph/products/PRODUCTS/PRINTERSFACSIMILES/INKJET/ALLINONEINKJET.aspx)

[http://www.canon.com.ph/PRODUCTS/PRINTERSFACSIMILES/INKJET/ALLINONEINKJET/PIXMAMP237.aspx](http://www.canon.com.ph/PRODUCTS/PRINTERSFACSIMILES/INKJET/ALLINONEINKJET/PIXMAMP237.aspx)

then for support and download it takes you to  [http://support-ph.canon-asia.com/](http://support-ph.canon-asia.com/)

and on to [http://support-ph.canon-asia.com/contents/PH/EN/0100469501.html?r=s&q=](http://support-ph.canon-asia.com/contents/PH/EN/0100469501.html?r=s&q=) and there is the scangearmp (debian)

---

