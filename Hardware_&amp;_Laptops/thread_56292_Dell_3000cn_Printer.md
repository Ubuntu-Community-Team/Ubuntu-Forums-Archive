---
title: "Dell 3000cn Printer"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by Jeffrae on 2005-08-12
Hello,

     I have a Dell 3000cn printer that is working beautifully on my Windows machine.

I have found information in other forums on getting it to work with linux, but I do not have any luck.

I have been selecting Generic PCL Drivers.  PCL 5 works, but print is not within the paper.  It is like every is scooted down an inch.  It always asks to load paper after printing.  Maybe I better keep my windows box around a little longer untill this printer plays well with UBUNTU... :)

I do beleive that this printer is a bebadged  Fuji-Xerox.. Mabe based on the DOCUPRINT C525A.

---

### Post by reto on 2005-11-29
Just got this printer, but I have no windows machine to compare with. 

Using the KDE "Add Printer Wizzard":
- Remote Printer (TCP)
- Insert the IP-number (which I found using the menu/display directly on the printer) and port 9100
- Select as Model "GENERIC -  PCL 6/PCL XL Printer"
- Change Settings to match my paper Format
-> Test-Print looks just fine but is in grayscale
-> changed configuration (same place as paper format) to color and with the display/menu on the printer Menu -> Configure -> PCL -> Color 

Did the same again adding using the driver "HP Color Laserjet 5500 (Foomatic+hpjs)", now the testpage comes with a black-border line (around 5-8 mm from the border of the paper) which didn't show up on the previous test-print.

---

### Post by reto on 2006-04-12
Keep getting the message "Load MPF Letter Plain 1", I don't have and I don't need US letter, and I configured the driver and checked on submitting the print-job to print it on A4.

---

### Post by reto on 2006-07-31
Got a change!

On the printer do the following: 
Select menu > tray settings> paper size > MPF> Free Size - enter to save.

While it asked for Letter when I had selected A4 it now just worked (don't know how long...)

---

