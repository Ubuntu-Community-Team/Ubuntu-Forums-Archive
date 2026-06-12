---
title: "Adding a LAN printer"
date: 2005-11-04
forum: Hardware &amp; Laptops
---

### Post by Diod on 2005-11-04
The printer is a OKI C3200n which is connected using its LAN port to the router. I use a driver supplied with the printer to install it on windows. I must use the OKI LPR Utility to do this in windows(so it gets recognized). So my question, simplified: how do i add a printer that is directly connected to a router in ubuntu.

---

### Post by Diod on 2005-11-04
Plz, i dont feel like putting everything i have to print on a USB stick and print it at my laptop :p

---

### Post by Diod on 2005-11-07
bump

---

### Post by bluetoad on 2005-11-07
You'll need the hostname or IP Address of the printer and the connection protocol details

1. Go to system/administration/printing
2. Click on New Printer
3. Click on Network Printer
4. Select how you connect to the printer - probably HP Direct or UNIX Printer (LPD)
5. Enter the Host and socket/queue details.


                                                                                ...Peter

---

### Post by Diod on 2005-11-11
I used TCP to connect to my printer now, but on the screen of my printer it says:

Data incorrect or timeout(loosely translated from dutch)

This is because i dont have a driver for linux, does someone know this?

---

### Post by bluetoad on 2005-11-11
I assume you meab lpd by that?  What that means is that your printer is running 
the equivalent of a Unix lpd daemon (traditional Unix printer protocol).  That listens on port TCP 515 by default.

To see if you can connect to printer you can try 

telnet thePrinterIPAddressOrHostname 515

to exit press ctl-] and then type quit.

If you are using the HPDirect protocol substitute the port for 9100 (or whatever port you specified).

So if you can't connect to it there is some network issue.

I just had a look under the printers and don't see your printer listed.  In the specifications does it say it does postscript or is PCL compatible or any clue like that.  Then you can choose an alternate printer.  For example, my Lexmark E230  is PCL compatible so I choose an HP LaserJet 3P w/PCL5


                                                                          ...Peter

P.S. The E230 is fine for an el cheapo - saves the pocket from using one of those Gobblejet printers.

---

### Post by Diod on 2005-11-12
To both 515 and 9100 it says its connected.
Ill research a little for which type of driver it uses

edit: Cant find anything about the drivers :/

---

### Post by bluetoad on 2005-11-14
I did a little searching for you and it doesn't look good.

The Australian OKI site ([http://australia.oki.com/fcgi-bin/public.fcgi?cid=159&pid=5&chid=1&pdflag=1&prid=533&prodname=C3200n&hex=611774&hex2=C8B2CE](http://australia.oki.com/fcgi-bin/public.fcgi?cid=159&pid=5&chid=1&pdflag=1&prid=533&prodname=C3200n&hex=611774&hex2=C8B2CE))
told me it used "Windows host based printing sytem"

I had a look on [www.cups.org](www.cups.org) and it doesn't look promising:

[http://www.cups.org/newsgroups.php?gcups.general+T+Qc3200n](http://www.cups.org/newsgroups.php?gcups.general+T+Qc3200n)

So you could try the GDI driver yourself and see if you have any luck.

                                                                 ...Peter

---

### Post by Diod on 2005-11-14
Cant get it to work :( oh well ill use a USB-stick when i wanna print something.
Thx for your help and time though :)

---

