---
title: "Applications freeze when I try to print"
date: 2008-08-03
forum: General Help
---

### Post by alexjohnc3 on 2008-08-03
Ubuntu is able to detect my printer, a HL-2070N, and print test pages from System -> Administration -> Printing -> Help -> Troubleshoot, but if I click "Print" on any application, the application freezes up and I have to Force Quit it.

---

### Post by alexjohnc3 on 2008-08-04
Bump.

---

### Post by alexjohnc3 on 2008-08-06
Can someone please help?

---

### Post by jonian_g on 2008-08-06
Try running an application from the terminal, try to print and look at the terminal for error messages and paste the output here.

---

### Post by alexjohnc3 on 2008-08-12
> **jonian_g said:**
> Try running an application from the terminal, try to print and look at the terminal for error messages and paste the output here.
I tried it with both Firefox and Gedit, but both froze when I clicked on "print" regardless of whether I opened them from the terminal or from an icon in the panel. I noticed OpenOffice worked fine though, regardless of whether I opened it in the terminal or I opened it normally.

I didn't get any error messages in the terminal. Is there some sort of command I need to enter for it to provide error messages, or should it do it automatically? Once the program has frozen, the terminal doesn't do anything and all I can do if force quit it. The terminal then says "Killed".

---

### Post by alexjohnc3 on 2008-08-20
Bump

---

### Post by public_void on 2008-08-20
Your printer is listed as needing the manufacturers driver on [linuxprinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2070N"). Brother provide linux support with instructions and a nice .deb package at [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html) . I'd suggest uninstalling your printer first before continuing with the instructions.

Also, to debug further problems your will need to edit /etc/cups/cupsd.conf. This is owned by root so sudo nano cupsd.conf. Then change the line starting with LogLevel, this tells CUPS to output more information to /var/log/cups/error_log when printing. Remember the change it back when the problem is fixed. It should look like this:
```
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning <------------ Change warning to debug

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
...
```Next restart CUPS with
```
sudo /etc/init.d/cupsys restart
```Now try printing. Post the contents of /var/log/cups/error_log. It will be large so use a paste bin site (e.g. [http://rafb.net/paste/](http://rafb.net/paste/)) or attach it to the post. If you look through it your looking for lines beginning with an E which is an error.

---

