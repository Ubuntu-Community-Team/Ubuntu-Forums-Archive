---
title: "Printer Problems"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by Khaine on 2006-02-15
I'm trying to install a remote printer attached to a windows xp pro machine.  However when I attempt to launch System | Administration | Printing nothing happens.

---

### Post by schdefan on 2006-02-15
does the printer appear in your list. Is it shared? Give some more information about your configuration.
schdefan

---

### Post by Khaine on 2006-02-16
Ok, yes the printer is shared.

See my main problem is that the printer settings gui won't display, and ages later there is an error box about not being able to connect to cupsd.  I've tried restarting the service, and it seems to start up ok.  This is what the logs of /var/log/cups say:

```

I [16/Feb/2006:15:58:25 +1100] Listening to 7f000001:631
I [16/Feb/2006:15:58:25 +1100] Loaded configuration file "/etc/cups/cupsd.conf"
I [16/Feb/2006:15:58:25 +1100] Configured for up to 100 clients.
I [16/Feb/2006:15:58:25 +1100] Allowing up to 100 client connections per host.
I [16/Feb/2006:15:58:25 +1100] Full reload is required.
E [16/Feb/2006:15:58:26 +1100] LoadAllPrinters: Unable to open /etc/cups/printers.conf - No such file or directory
E [16/Feb/2006:15:58:26 +1100] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [16/Feb/2006:15:58:32 +1100] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...I [16/Feb/2006:15:58:33 +1100] LoadPPDs: No new or changed PPDs...
I [16/Feb/2006:15:58:33 +1100] Full reload complete.

```

---

### Post by schdefan on 2006-02-16
You can open cups configuartion tool in a browser
[http://localhost:631](http://localhost:631)

If there is no printer.conf file you hav to create one. Type in a terminal
```
$ locate cupsd.conf

/etc/cups/cupsd.conf
/usr/share/man/fr/man5/cupsd.conf.5.gz
/usr/share/man/es/man5/cupsd.conf.5.gz
/usr/share/man/man5/cupsd.conf.5.gz
/usr/share/apps/kdeprint/cupsd.conf.template
```

schdefan

---

### Post by Khaine on 2006-02-16
When I try going to localhost:631 or 127.0.0.1:631 the connection times out, nothing is displayed

---

### Post by schdefan on 2006-02-17
try to reinstall cups

---

