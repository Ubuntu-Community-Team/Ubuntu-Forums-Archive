---
title: "Printer stopped working after upgrade"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by Priceguy on 2007-11-20
My printer stopped working after I upgraded to 7.10. The job becomes Stopped and when I try to cancel I get "There was an error during the CUPS operation: 'client-error-not-possible'". The printer doesn't react. Ubuntu can detect the printer and install the driver without problems. It's an HP DeskJet 710C. I have restarted the printer service.

---

### Post by 1/0 on 2007-11-20
Sounds like a permissions problem I had a while ago. I can't remember how I did it but you could always try to remove the printer in CUPS ([http://localhost:631](http://localhost:631)), restart cups and hplip. Then add and setup the printer again.

---

### Post by Priceguy on 2007-11-20
I have tried removing the printer, stopping the printer service, starting it, and then adding the printer again, to no avail. I can't find anything called hplip, what's that?

---

### Post by 1/0 on 2007-11-20
Hplip contains the drivers for your printer (could also be hpijs, foomatic, ghostscript or pnm2ppa  btw). I would check/reinstall them. It could be that foomatics is not properly updated during the upgrade. You might want to (after checking the above):

```
foomatic-configure -s cups -p HP-DeskJet_720C -c file:/dev/lp0 -n hp720c -d pnm2ppa
```

Where the printer name comes from /usr/share/foomatic/db/source/printer/

```
ls /usr/share/foomatic/db/source/printer/ |grep 710
```

---

### Post by Priceguy on 2007-11-20
OK, something's different anyway. I found the printer names in /usr/share/foomatic/db/source/printer/ and /etc/cups/ppd/ and inserted them in your code, and after fixing all permissions I needed it seemed to work. No error messages.

When I try to print from OpenOffice now, I get an error message from OpenOffice reading "Error while printing". When I try to print from gedit, I get the same result as before: Job becomes Stopped.

---

### Post by Priceguy on 2007-11-22
I found [this bug report](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/133818/comments/5), that may have something to do with it, even though my printer is a HP, not a Brother. /opt is completely empty on my machine, so if the drivers have to be there (as the bug report says) that is certainly the problem. In /etc/apparmor.d/usr.sbin.cupsd I can't find anything pertaining to my printer, but I haven't been able to work out how to change the bug report's advice to fit my printer.

---

### Post by 1/0 on 2007-11-22
Well, its probably something with how Openoffice communicates with Ubuntu. Try reinstalling openoffice. I know some people got it working by using the binaries from the ooo homepage. I would personally prefer finding the problem before installing non-Ubuntu programs. Before you used to be able to do spadmin but spadmin is deprecated (oo uses cups instead, which is better). Try reinstalling openoffice and see if the printer is updated.

---

### Post by Priceguy on 2007-11-22
I can't print from anything other than OpenOffice either, so I can't really see how it could be OpenOffice.

---

### Post by 1/0 on 2007-11-22
> **Priceguy said:**
> OK, something's different anyway. I found the printer names in /usr/share/foomatic/db/source/printer/ and /etc/cups/ppd/ and inserted them in your code, and after fixing all permissions I needed it seemed to work. No error messages.

When I try to print from OpenOffice now, I get an error message from OpenOffice reading "Error while printing". When I try to print from gedit, I get the same result as before: Job becomes Stopped.

I thought it worked except in OOO. Does it work differently if you print as root, i.e. permissions problem?

Any thing in dmesg?

```
sudo dmesg |tail
```

Anything in the cups error log (log level can be set in cupsd.conf). Also check that you have something like this in cups.conf:

```
<Location /admin>
Order allow,deny
Allow localhost
</Location>
```

Anything in messages?

```
tail -f /var/log/messages
```

Also, just to triple check, pnm2ppa is installed, right?

---

### Post by 1/0 on 2007-11-22
Hey, I think I found your solution! 

```
sudo aa-complain cupsd
```

It was on the [Linux Printing Homepage]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_710C")

---

### Post by Priceguy on 2007-11-22
Yes, that was it. It's working perfectly now. Thank you very much.

---

