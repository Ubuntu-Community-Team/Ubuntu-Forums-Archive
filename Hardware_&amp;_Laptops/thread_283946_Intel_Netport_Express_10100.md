---
title: "Intel Netport Express 10/100"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by SuperMau on 2006-10-24
I was looking for some help with printing to my network print server, an Intel Netport Express 10/100, from my "New Ubuntu" box (Good bye M$ Windows Genuine Advantage and Microsoft) :D  but could not find any posts about it so I would like to post the very easy process.

1) Go to System->Administration->Printing
2) Double Click "New Printer"
3) Select "Network Printer" with "HP Jetdirect"
4) In the host section enter the print server IP address
5) In the port section enter:
[INDENT]LPT1_PASSTHRU or LPT1_TEXT (for parallel port 1 or the internal card)
LPT2_PASSTHRU or LPT2_TEXT (for parallel port 2)
COM1_PASSTHRU or COM1_TEXT  (for the serial port)
Use PASSTHRU for PCL or PostScript* files and TEXT for standard 
UNIX text files[/INDENT].
6) Click Forward and Enter Manufacturer, Model and Forward
7) Enter a Name, Description and Location for you to recognize
8) Go through the properties pages of your newly created printer to configure paper, etc...

Hope this helps!!!

---

### Post by Shawn Reist on 2007-01-05
Hello,

I am new to Ubuntu, and Linux though I have played a little with Linux since Red hat 5.x and Mandrake 7 & 8 ... but would still consider myself new.

I also have a Intel Netport Express pro/100 and have tried several attempts to get it to work with Linux. I have even tried the setup that you have written with no success..

-----------

1) Go to System->Administration->Printing
2) Double Click "New Printer"
3) Select "Network Printer" with "HP Jetdirect"
4) In the host section enter the print server IP address
5) In the port section enter:

    LPT1_PASSTHRU or LPT1_TEXT (for parallel port 1 or the internal card)
    LPT2_PASSTHRU or LPT2_TEXT (for parallel port 2)
    COM1_PASSTHRU or COM1_TEXT (for the serial port)
    Use PASSTHRU for PCL or PostScript* files and TEXT for standard
    UNIX text files

.
6) Click Forward and Enter Manufacturer, Model and Forward
7) Enter a Name, Description and Location for you to recognize
----------------

I can't for some reason with the proinstall utility that Intel supplies, get past the printer name part of the install procedure. I have tried several things and have been able to print a test page. but after the initial print test page everything else is garbage.

I am presently trying to read various posts and docs on LDP, Linux printing, netcat...

---

### Post by Shawn Reist on 2007-01-05
I got it working....

Mmm... wonder if I am the only one reading this or typing to self?

Anyway to configure printing to the Intel Netport Express pro/100 print server I opened Firefox and logged into cups 1.2.4. I am using Ubuntu6.10, Edgy

*note: static IP for my print server is 192.168.1.98. Use the IP for your setup I had also added to the hosts file /etc/hosts.*

**[http://localhost:631](http://localhost:631)**

add printer

[B]Name:
Location:
Description:[/B]

next

**Device: LPD/LPR Host or Printer**

next

    lpd://hostname/queue

**lpd://192.168.1.98/LPT1_PASSTHRU**

next

**Make** and **mode**l of printer or PPD file if you have one

Done.. 

I even did a reboot and the printer still worked...

---

### Post by cyrilp on 2007-12-16
I have tried everything that you did but I am unable to print. I have a Lexmark Optra R+ printer and am using a Intel Netport 10/100 Express print server. The IP address is 192.168.1.2. I did everything that you did except the entry to the hosts file.

Device:LPD/LPR Host or Printer
lpd://192.168.1.2/LPT1_PASSTHRU
make/model using PPD for my printer

I get the message "Unable to connect - timeout" It sees the printer but just does not talk to it

Looking on the Windows computers the port is listed as 515. Do I do anything with this?

What do I put in my /etc/hosts file?

Thank you in advance for your help

---

### Post by SuperMau on 2007-12-20
Ok, the configuration I first posted was done on Dapper. The only problem I had with Feisty was that it asked for a password and since my user was not part of the lpadmin group (since *Printer Configuration *is a front end to CUPS as I understand) it did not work.

I made my user a member of the lpadmin group and added the printer the same way explained on my first post:

**1.** Click on *System->Administration->Printing* and on the *Printer Configuration* window make sure you can change and apply settings, if so, you can go ahead and add the printer clicking on *New Printer*.

**2.** In Host Name enter the static IP of the print server. In Port number enter LPT1_PASSTHRU, LPT2_PASSTHRU or COM1_PASSTHRU. I used LPT1 for a Laserjet 5MP printer I have connected to LPT1 port.

**3.** Select the make of the printer or provide a PPD file (windows driver disk should have one if your printer supports PostScript).

**4.** Select model and driver.

**5.** Enter a printer name, description and location... Click *Apply *and enjoy.


I did not try the "LPD/LPR Host or Printer" that Shawn Raist mentions but I guess it should work too. I did not use any Intel software or anything else.

By the way, the print server should be in your subnet and the configuration web page (ex: [http://192.168.0.6](http://192.168.0.6)) reachable from the workstation you want to print from or else you shoul create a network route to it.

I include a snapshot showing the new printer.

I hope this helps...

SuperMau®

---

### Post by Shawn Reist on 2007-12-27
Hello,

well I tried both ways... through the menu

Click on System->Administration->Printing and on the Printer Configuration window make sure you can change and apply settings, if so, you can go ahead and add the printer clicking on New Printer.

same as SuperMau, and was unable to get the printer working..

I was able to get the printer working through CUPS

[http://localhost:631](http://localhost:631)

and adding the printer there...  I have recently reflashed my Netport and here are the settings from the device, changed router and static IP address

Model : Intel Netport Express Pro/100 print server, 
Flashed with Bios : V4.46a
Static IP  : 192.168.0.98
Printer : HP LaserJet 1100

Basic Flash defaults

hope this helps

---

