---
title: "Feisty holds my print job until &quot;specified&quot; (why, because of user rights?)"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by nnixy on 2007-07-11
Hello! 

I have a computer with Feisty, and after I double click on the driver icon for my printer and send a test page the status window says pausing: job-hold-until-specified, and the page is not printing. :(

I wonder whether anyone here knows how I can make the job become "specified" and print? Also, in the printer properties window there is a message saying ".. /usr/lib/cups/backend/lpd failed". So what makes lpd fail? 

It is possible to print from another computer using Windows XP so it seems to be a problem with my settings in Feisty. However I'd say the printer driver is installed in the proper way, or at least I followed a procedure with which I was successful in a previous installation of Feisty on the same computer, and in which the printing worked. 

However, one difference is that now there are several user accounts, whereas in the previous installation there was only one. This makes me suspect that the problem may be related to user rights, but I am not sure. 

The stuff: 
Printer:   Brother HL2070N
Print Server:   DLink 301P+ with an IP address, 
Drivers:   *cupswrapperHL2070N-2.0.1-1.i386.deb* and *brhl2070nlpr-2.0.1-1.i386.deb*

I modified the printer in *[http://localhost:631](http://localhost:631)* according to the following instructions:
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html)
[http://solutions.brother.com/linux/sol/printer/linux/cups_network.html](http://solutions.brother.com/linux/sol/printer/linux/cups_network.html)
[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2070N](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2070N)

I appreciate any help or advise. 

Regards, nnixy

---

### Post by nnixy on 2007-07-11
OK, I solved it by uninstalling the deb files, and reinstalling them again. After looking at a Ubuntu Hardware Compatibility List I selected the hl1250.ppd (not the hl2070N.ppd). Not sure if this was the best solution, but now I can print. :)

---

### Post by amias on 2008-02-03
This happend to me as well on ubuntu studio , i fixed it by switching to the gutenprint ppd for my
printer instead of the hpijs one . It would seem that hpijs doesn work over the network , although
that is what is in use at the other end.

---

