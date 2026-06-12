---
title: "problem printing to lexmark e120n over network"
date: 2011-06-19
forum: Hardware
---

### Post by mmoalem on 2011-06-19
hi there all - recieved a network printer (lexmark e120n) which i connected to my home network using ethernet. it works fine printing from windows xp but not from my ubuntu natty. ubuntu finds it allright and automaticly find and install the driver (e120n foomatic/postscript). the laptop will go through the printing process notifying me that it was sent to the printer but the printer is not printing nada. it wont even print the self-test page.
any idea what i should do?
cheers
michel

---

### Post by Kirboosy on 2011-06-19
Hi Michel,

Try removing the printer and re-adding it manually by typing in the IP address. I have a Brother Network Printer and it seems this is the only way to get it to work properly.

Hope that helps and its a simple solution.
~Caboose

---

### Post by walt.smith1960 on 2011-06-19
> **Caboose885 said:**
> Hi Michel,

Try removing the printer and re-adding it manually by typing in the IP address. I have a Brother Network Printer and it seems this is the only way to get it to work properly.

Hope that helps and its a simple solution.
~Caboose

Like Caboose, I have a couple networked Brother printers.  I don't have first-hand experience with Lexmark.   You're fortunate that your Lexmark printer does what it does; Lexmark is notorious in the desktop Linux world and not in a good way.  I've had the best success by typing in the "device URI" box the following: "socket://xxx.xxx.xxx.xxx:9100"  where x represents the I.P. address digits. This has been reliable for me.  My automatic install uses "dnssd://something......".  That has proven unreliable over time for me.  The other thing you could try would be to type the following in a browser window: "http://localhost:631/printers" and see if anything interesting pops up.

---

### Post by mmoalem on 2011-06-19
Hi Caboose - thank you very much for taking the time to suggest your solution but cant figure out where to input the ip address manually as you suggested...
cheers
michel

---

### Post by mmoalem on 2011-06-19
> **walt.smith1960 said:**
> Like Caboose, I have a couple networked Brother printers.  I don't have first-hand experience with Lexmark.   You're fortunate that your Lexmark printer does what it does; Lexmark is notorious in the desktop Linux world and not in a good way.  I've had the best success by typing in the "device URI" box the following: "socket://xxx.xxx.xxx.xxx:9100"  where x represents the I.P. address digits. This has been reliable for me.  My automatic install uses "dnssd://something......".  That has proven unreliable over time for me.  The other thing you could try would be to type the following in a browser window: "http://localhost:631/printers" and see if anything interesting pops up.
hi there walt and thank you too for the reply - tried inserting the ip into uri field as suggested and tried the [http://localhost:631/printers](http://localhost:631/printers) option, tried to print a test page from there and tried to add new printer through there and still no joy...

---

### Post by RedRat on 2011-06-19
I must say that I have had good luck with technical support from Lexmark. Did you download the Lexmark drivers from their web site? Install them. 

I have a Lexmark 905 Platinum multifunction wireless printer and had no problem installing the appropriate drivers for 32bit 8.04. Installing the 64bit drivers for my 10.04 installation was a bit tough. But between the experts at both Lexmark and System76 I got the drivers to work. You might try calling Lexmark and see if you can get some phone help, I found them to be quite good. 

So far Lexmark has been extremely helpful when I have had problems with their printer.

---

### Post by chubinator on 2011-07-16
> **mmoalem said:**
> hi there all - recieved a network printer (lexmark e120n) which i connected to my home network using ethernet. it works fine printing from windows xp but not from my ubuntu natty. ubuntu finds it allright and automaticly find and install the driver (e120n foomatic/postscript). the laptop will go through the printing process notifying me that it was sent to the printer but the printer is not printing nada. it wont even print the self-test page.
any idea what i should do?
cheers
michel

I had the same issue with the same printer. Try changing the driver from the Postscript to the PCL5.  That worked for me.  The bummer is that you can no long view the ink levels/etc from the desktop, but it works.

---

