---
title: "Serial Printer"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by nhartley on 2006-01-12
Could someone please help me install a serial printer?


Though I can do amazing things in the MS world, I have been humbled by the realization that I can not even add a serial printer to my Ubuntu 5.10 machine.

Because of a bug between CUPS and my SMC gateway router that causes the printer to print a job separator page plus a blank page for every print job, I have been forced to plug my HP Laserjet 4 in via the Serial port. I figured it would take me all of 2 minutes to plug it in, add a new printer profile and get to work printing out a report for my kids on my nifty Ubuntu machine. No such luck.... 

My options for the Printer Port are shy a serial port:
 hp no_device_found
 Parallel Port #1 (Cannon)
 Parallel Port #2 (EPSON)
 Parallel Port #1
 USB Printer #1...16

I have searched for hours and have found nothing but dead ends.

Even pointing me right direction would greatly appreciated.

Thanks,

---

### Post by tim15856 on 2006-01-12
You might want to think about connecting it to a print server or install a jetdirect card. A new print server will cost $30-40. Cheaper ones can be bought on ebay.

---

### Post by nhartley on 2006-01-17
[QUOTE=tim15856]You might want to think about connecting it to a print server or install a jetdirect card. A new print server will cost $30-40. Cheaper ones can be bought on ebay.[/QUOTE]

Is this to say that printing to a serial printer is difficult?

---

### Post by cory lee on 2006-02-16
here is an answer 
chmod a+rw /dev/ttyS0
chmod +xrw /dev/lib/cups/backend/serial
/etc/init.d/cups restart
there is a bug also if here is no backend/serial 
see backend-available/serial
right click make a link  copy to backend directory and restart computer or cups
do lpinfo -v 
should show up now.
my problem is /dev/ttyUSB not shown... oh well not much help in the forums sometimes...

---

### Post by nhartley on 2006-02-17
Thanks for your help, from what I have read this is on the right track however....

I can not find /dev/lib/cups/backend/serial or anything close.

---

### Post by joen on 2006-03-27
nhartley: he meant /usr/lib/cups/backend/serial

to make the link he's talking about from the CLI:

ln -s /usr/lib/cups/backend-available/serial /usr/lib/cups/backend/serial


This is a really annoying bug!

---

