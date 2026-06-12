---
title: "Lexmark Laser Printers"
date: 2005-03-16
forum: Hardware &amp; Laptops
---

### Post by grenadier on 2005-03-16
Lexmark receive a lot of flak for being difficult to install in Linux.

My printer is the Lexmark E232 Mono Laser Printer that has been successfully installed in a number of Distributions.

To-day I installed it in Mepis, info from The Printer Test Page is as follows,

Postscript: Level 3
Version: 3010 (707)
Product: ESP Ghostscript
Serial #: 42
Printed Using Cups v1.1.x

This printer, model E232, connected to a parallel port, was installed via Kde Printing Manager.

Generic PCL 6/PCL XL Printer (FOOMATIC + pximono) was selected.

What is important, is to select the settings suitable for the printer before making a Test Print. 
These settings, include,
Printout Mode:
Page Size:
Media Source:
Color Mode:
Resolution:
Get these wrong and it won't print.

The Linux driver for the E232 covers a very large range of printers, but I haven't had to use this driver.
-------------------------------
Grenadier ;)

---

### Post by psyke on 2005-03-25
i also have a E232 but usb-connected and it took me a while to get it work!

under warty the HP laserjet series PCL 6 driver work great!
now i use generic PCL-6/PCL-XL-Printer and they work too, but i can't tune the settings !
they are empty and grey...


does anyone else have expirience with this printer?

---

### Post by Nathaniel Firethorn on 2005-03-26
I have a similar problem. I'm trying to get a Lexmark E222 to print from the live cd before I complete the install. The printer's detected just fine, but anything printed goes into hyperspace.

/var/log/cups/error_log contains the following after an attempt to print the test page:

> Unable to convert file 0 to printable format for job 9!

Do you have ESP GhostScript installed?I take it that this CUPS thing does not work with /etc/printcap?

Does the live disk come with ESP Ghostscript installed?

Thanks,
- nf

---

### Post by grenadier on 2005-03-27
psyke wrote> i also have a E232 but usb-connected and it took me a while to get it work!

under warty the HP laserjet series PCL 6 driver work great!
now i use generic PCL-6/PCL-XL-Printer and they work too, but i can't tune the settings !
they are empty and grey... 

Yes, in Gnome the settings are greyed out. These settings facilities are available in KDE.

One drawback of using the Generic printer is Toner settings are not available.

grenadier

---

### Post by h4ck on 2005-09-18
hy! 
i am new at ubuntu and i have a lexmark e232 ! What do i need to to To ger working help! TNx

H4ck

---

### Post by Den-Can on 2007-04-20
Here some help for Lexmark E232 laser printer user...In the printer installation ( printer selection panel ) simply put HP Laserjet ( Just Laserjet .. no model number ) .. Works great here ...

---

