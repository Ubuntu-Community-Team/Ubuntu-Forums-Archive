---
title: "Drivers for Epson SX600FW"
date: 2008-11-15
forum: Hardware
---

### Post by pieroxy on 2008-11-15
Hello,

I am using Ubuntu 8.04 and I just bought multi-purpose printer/scanner Epson SX600FW. While trying to install it on Ubuntu is is detected but the driver cannot be found... My printer is connected to my Wifi Network.

Can I use another driver? Or where can I find the right driver?

Also, how to install the built-in scanner?

Thanks a lot.

---

### Post by apacheuk on 2008-11-16
try the following site....

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Office_SX600FW]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Office_SX600FW")

I followed those instructions and got the printer working over wifi on both 8.04 and 8.10

---

### Post by teaker1s on 2008-11-16
and check avasys epson site
[http://avasys.jp/hp/menu000000500/hpg000000442.htm]("http://avasys.jp/hp/menu000000500/hpg000000442.htm")

---

### Post by pieroxy on 2009-02-20
I upgraded to 8.10 and everything is fine. Much smoother considering I had to upgrade anyways ;-)

Thanks

---

### Post by robenroute on 2009-03-06
Just wanted to let people know that my newly acquired Epson BX600FW works wonderfully well on 8.04 (Hardy). XSane recognized the scanner without problems. Also, the iscan program from [avasys]("http://avasys.jp/hp/menu000000500/hpg000000442.htm") works.

I installed the gutenprint drivers (available [here]("http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.2-1lsb3.2_i386.deb") -- 64-bit package is also available) and CUPS even suggested the correct printer driver while going through the setup.

Just happy as a pig in the proverbial sh..  ;-)

P.S. I haven't tried 8.10 (Ibex) yet, but I doubt there will be any hiccups.

---

### Post by pieroxy on 2009-03-07
Does anyone know how to put this thread [SOLVED] ? I don't remember or it has changed...

thanks

---

### Post by robenroute on 2009-03-07
> **robenroute said:**
> Just wanted to let people know that my newly acquired Epson BX600FW works wonderfully well on 8.04 (Hardy). XSane recognized the scanner without problems. Also, the iscan program from [avasys]("http://avasys.jp/hp/menu000000500/hpg000000442.htm") works.

I installed the gutenprint drivers (available [here]("http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.2-1lsb3.2_i386.deb") -- 64-bit package is also available) and CUPS even suggested the correct printer driver while going through the setup.

Just happy as a pig in the proverbial sh..  ;-)

P.S. I haven't tried 8.10 (Ibex) yet, but I doubt there will be any hiccups.

Well, I've got it printing via the network (both wireless and cable), but scanning via the network doesn't seem to work: XSane mentions there are no devices available and Image Scan says it could not send command to scanner, and if I want to check the scanner's status...

This is all on Ibex.

Anyone?

---

### Post by pieroxy on 2009-03-14
I actually have the same issue. Printing works fine but I coundn't get the scanner to work via Ethernet....

Does anyone have a clue?

---

### Post by kerneloftruth on 2009-03-16
*subscribes*

I'll be seen getting one of that or the BX600FW

so tracking this thread ...

do the avasys drivers for printing work also ? anyone tried them ?

I'm seeing the gutenprint driver as a kind of last resort since they are told to consume much more ink ...

thanks

**update:**

the printer I ordered had the infamous paper jam bug from the start so I ordered a printer from a different company ...

---

### Post by nvidia7 on 2013-04-15
The driver doesn't work for me. I downloaded the latest Epson driver from avasys and installed it for CUPS but in that case the printing never starts with an error.[TABLE="class: list"]
[TR]
[TD][EPSON_Stylus_SX600FW]("http://localhost:631/printers/EPSON_Stylus_SX600FW")[/TD]
[TD]EPSON Stylus SX600FW[/TD]
[TD][/TD]
[TD]Epson Stylus SX600FW, Epson Inkjet Printer Driver (ESC/P-R) for Linux[/TD]
[TD]Idle[/TD]
[/TR]
[/TABLE]


[TABLE="class: list"]
[TR]
[TD][EPSON_Stylus_SX600FW]("http://localhost:631/printers/EPSON_Stylus_SX600FW")-12[/TD]
[TD]Test Page[/TD]
[TD]root[/TD]
[TD]1k[/TD]
[TD]Unknown[/TD]
[TD]  canceled at
Wed 10 Apr 2013 06:03:52 PM CEST 
*"/usr/lib/cups/filter/pdftoraster failed"*[/TD]
[/TR]
[/TABLE]

Looking at the logs closely:
  
[http://pastebin.ca/2360153](http://pastebin.ca/2360153)

Pls help. The printer working completely fine from windows.

---

### Post by oldos2er on 2013-04-16
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

