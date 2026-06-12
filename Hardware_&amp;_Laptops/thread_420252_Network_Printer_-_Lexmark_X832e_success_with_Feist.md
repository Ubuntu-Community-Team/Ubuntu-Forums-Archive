---
title: "Network Printer - Lexmark X832e success with Feisty"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by ariel on 2007-04-23
Hi, this is micro-howto setting up Ubuntu 7.04 (feisty) to print to a Lexmark X832e  Network Printer, with double-side printing support, commonly used in corporate environments.

First a word: typically you would like to log in to the Windows Domain Controller, and access the printer via the print server. That would be the 'cleanest' solution. The follow is a quick hack to get the job done quickly, printing directly over the "raw" (tcp socket) interface.

1) Obtain the IP address of the network printer. To do this, from the printer panel, select UTILITIES and press [Select], then look for PRINT NET  SETUP and press [Select]. From the TCP/IP section of the printout, note the printer's IP address (a.b.c.d, in the following paragraphs)

2) In you Ubuntu desktop, select System > Administration > Printing; this will open the Printers window

3) In the Printers window, go to the menus and select Printers > Add Printer; this will open the Add a Printer window; in it, configure the following:

    Printer Type = Network Printer; 
    In the type selection list, select "TCP/Socket, HP JetDirect, Raw Connection"; 
    Host = a.b.c.d
    Port = 9100

    When done with all the settings, click the [Forward] button

4) The Step 2 of "Add a Printer" shows up; select the following:

   Manufacturer = Lexmark
   Model = Optra W810
   Driver = Postscript

    When done with all the settings, click the [Forward] button

5) The step 3 of "Add a Printer" shows up; enter a description for the printer, and change the name to Lexmark X832e, and you are nearly done. Click [Apply]

6) In the Printers window, you will now see your Lexmark X832e icon; right click on it and select Properties. 

7) Click on the paper tab and select
   Paper size = set as needed (US/Canada: typically Letter)
   Source = Default
   Double Sided = Long Edge (standard) 

8) Click "Print a Test Page"

Done!

ps. good luck!

---

