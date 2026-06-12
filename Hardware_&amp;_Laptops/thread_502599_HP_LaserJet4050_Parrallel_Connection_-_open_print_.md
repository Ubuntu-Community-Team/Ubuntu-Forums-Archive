---
title: "HP LaserJet4050 Parrallel Connection - open print channel failed"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by wadesmart on 2007-07-16
I was given this really nice HP LaserJet 4050 but getting it installed has been a problem.  My system is Ubuntu Fiesty. I installed via the Printers Menu and it was recognized right away. However, whenever I try to print I received the following error:
Code:

Jul 16 19:46:54 wadesmart parport0: INFO: open print channel failed; will retry in 30 seconds... 


Shown here: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4050](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4050)
the printer is used via linux but after trying many drivers, it seems the main issue is this print channel. Even asking on the ubuntu list I have received no solutions.

Wade

---

### Post by jnorthr on 2007-07-21
Do you use a parallel cable to connect to lpt1 ? or a USB connection ?
Does your BIOS show the parallel port uses ECP protocol, bi-directional or just output only ?
Did you turn your printer on first before you powered on your system ?
The CUPS printer services must also be running. Think it's the 'lp' or 'lpd' command. Will go check mine to see...

---

### Post by wadesmart on 2007-07-21
I do use a parallel cable - as indicated in the subject line. However, I discovered that while I can send a command manually to the printer, it very clearly states in the information for HP (I discovered way after the fact) that on linux I cannot use a parallel cable but only a usb cable. 
My other printer, a ink jet, worked fine on parallel that is why I was stumped. So, I am acquiring a parallel to usb cable for the print now.

---

### Post by jnorthr on 2007-07-23
The ink jet uses parallel and works but the hp4050 does not ? Sounds more like the hp4050 printer is too smart, but good news then. Pls advise if this corrected your problem as i have an HP1320 capable of both parallel port and, as an alternative, usb connection. I have not tried to hook it up yet as i'm having trouble getting a parallel port zip100 drive to work before i go that far.:roll:

---

### Post by Tschortscho on 2007-11-08
Hi wadesmart,

I recently got myself an HP LaserJet 4050N printer for a few quid and I think I'm having the same kind of trouble you had. 

> **wadesmart said:**
> it very clearly states in the information for HP (I discovered way after the fact) that on linux I cannot use a parallel cable but only a usb cable.

Are you referring to the info on [http://hplip.sourceforge.net/supported_devices/laser.html](http://hplip.sourceforge.net/supported_devices/laser.html) ?

> **wadesmart said:**
> So, I am acquiring a parallel to usb cable for the print now.

Did this solve the problem?

Many thanks for your reply.

---

### Post by wadesmart on 2007-11-08
I did not get it to worth with the parallel cable. 

Try a usb cable instead. That should work. Apparently the parallel cable is not supported. 

Wade

---

### Post by stchman on 2007-11-08
> **wadesmart said:**
> I was given this really nice HP LaserJet 4050 but getting it installed has been a problem.  My system is Ubuntu Fiesty. I installed via the Printers Menu and it was recognized right away. However, whenever I try to print I received the following error:
Code:

Jul 16 19:46:54 wadesmart parport0: INFO: open print channel failed; will retry in 30 seconds... 


Shown here: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4050](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_4050)
the printer is used via linux but after trying many drivers, it seems the main issue is this print channel. Even asking on the ubuntu list I have received no solutions.

Wade

I have a 4050tn that works perfectly with Ubuntu.  I bring up the printer manager, select add new printer and it detect it right there.

According to [www.linuxprinting.org](www.linuxprinting.org) the 4050 is well supported using the Postscript driver.

---

### Post by wadesmart on 2007-11-08
What cable are you using?

---

### Post by Tschortscho on 2007-11-15
Just got myself a USB to parallel printer cable. I plugged in the cable, added the printer with the CUPS web-based configuration tool and now the printer works like a charm! :)
Thanks Wade.

---

### Post by wadesmart on 2007-11-15
GREAT!

Glad to hear it.

---

### Post by fbrauer on 2008-05-14
I got my HP 4050 working with a parallel cable by installing the generic PostScript driver (instead of HP 4050), set to 600 dpi.

---

### Post by wadesmart on 2008-05-15
I had read that online but I was not able to get that to work. 

Glad to see you did though.

---

