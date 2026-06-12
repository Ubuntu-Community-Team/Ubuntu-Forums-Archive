---
title: "Do I need to download drivers"
date: 2005-01-05
forum: Installation &amp; Upgrades
---

### Post by J.K. on 2005-01-05
i see that my printer is on the list when i entered the details, but still no printing. Do i need to get drivers for it.?

---

### Post by tiiim on 2005-01-05
[QUOTE=J.K.]i see that my printer is on the list when i entered the details, but still no printing. Do i need to get drivers for it.?[/QUOTE]
 im  having that problem too i think you have to add the path in menu or choose the usb port, nebody else can help?

---

### Post by randy on 2005-01-05
We'll need more information to help.  What printer is it? What type of connection?  Did you receive any error messages?

---

### Post by ankitmalik on 2005-01-05
Same problem :(

I have a Canon xnu i255!

---

### Post by hardcandy on 2005-01-05
[http://www.linuxprinting.org/printer_list.cgi?make=Canon](http://www.linuxprinting.org/printer_list.cgi?make=Canon) shows what I suspected, it is not supported yet. I have an i320, I use the drivers from turboprint. But they cost $30- oops $35 now with the exchange rate, there is a trial version, but it puts a turboprint logo on each page. 
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

I figured with the cost of the printer at around $30 on sale and the driver at $30, it was about the same as getting as getting a different printer, plus trying to configure a driver for a different printer would be more work. But the driver does work very well.

---

### Post by J.K. on 2005-01-05
[QUOTE=randy]We'll need more information to help.  What printer is it? What type of connection?  Did you receive any error messages?[/QUOTE]
Hi
Its a Lexmark 1100, I don't get any error msg, in fact it tells me that it has sent the print job. Everything act as if it had printed, and yes, the printer is plugged in:), 
In the sys config->printers window, the printer icon is displayed there, It says Lexmark printer(0 jobs). 
The printer is connected via a cable, not a USB port. I think its a serial cable.

---

### Post by ankitmalik on 2005-01-05
That is the problem with Linux. And not at all because of Linux!

These idiotic companies dont want to share info with the open world! Morons!

And to say Canon is said to be very Linux friendly!

---

### Post by tiiim on 2005-01-05
[QUOTE=ankitmalik]That is the problem with Linux. And not at all because of Linux!

These idiotic companies dont want to share info with the open world! Morons!

And to say Canon is said to be very Linux friendly![/QUOTE]
 mine says got drivers says it send the job and printing but nothing there...

---

### Post by hardcandy on 2005-01-05
For the Lexmark 1100:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-1100](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-1100)

---

### Post by tiiim on 2005-01-05
[QUOTE=hardcandy]For the Lexmark 1100:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-1100](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-1100)[/QUOTE]
 hp psc 1205?

but when i go to site i add driver and says already installed..

---

### Post by hardcandy on 2005-01-05
What print spool are you using? LPD or CUPS?

---

### Post by tiiim on 2005-01-05
[QUOTE=hardcandy]What print spool are you using? LPD or CUPS?[/QUOTE]
 on connection tab its local printer. cos its attached to my comp. it also has not detected any printer on the detected printer side...

---

### Post by tiiim on 2005-01-05
[QUOTE=tiiim]on connection tab its local printer. cos its attached to my comp. it also has not detected any printer on the detected printer side...[/QUOTE]
 i think driver under cups so how do i tell cups in the dialog to go to local machine?

---

### Post by hardcandy on 2005-01-05
[http://www.linuxprinting.org/cups-doc.html](http://www.linuxprinting.org/cups-doc.html)   ,start with step 5. The Cups admin tool is accessed via your web browser.

And you may need to restart cups, not sure about that but just in case;
"sudo /etc/init.d/cupsd restart"

---

### Post by tiiim on 2005-01-05
[QUOTE=hardcandy][http://www.linuxprinting.org/cups-doc.html](http://www.linuxprinting.org/cups-doc.html)   ,start with step 5. The Cups admin tool is accessed via your web browser.

And you may need to restart cups, not sure about that but just in case;
"sudo /etc/init.d/cupsd restart"[/QUOTE]
 cant login to localhost! is this a Ubuntu root prob then? lol

---

### Post by hardcandy on 2005-01-05
You may have to create a root password.
"sudo passwd root" then try that password for cups.

---

