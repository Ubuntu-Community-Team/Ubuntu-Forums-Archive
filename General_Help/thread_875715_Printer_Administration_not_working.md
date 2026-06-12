---
title: "Printer Administration not working"
date: 2008-07-31
forum: General Help
---

### Post by sholla on 2008-07-31
I installed Ubuntu 8.0.4 (Hardy, i think) a couple of days ago, and i felt almost ready to make the final change from Windows as I'm also planning to get Win4Lin.

I connected my printer, HP 1020 and the OS promptly flashed me a message saying the printer has been detected and installed. That was cool! When I attempted to print a document to it from OpenOffice Writer, nothing came out of the printer. I went to System->Administration->Printer to see if the printer need manual configuring, but the Printers Management app didn't display. So, I'm stuck.

How can I get the Printer Management app to work and also how to manage other hardware like scanners, though my scanner was detected and promptly installed and I was able to scan.

Thanks, guys.

---

### Post by ModelM on 2008-07-31
That printer control panel is just a front-end for CUPS, the brains behind all the printer operations.

You can skip the middleman & connect directly to CUPS for configuration by pointing your webbrowser to:

127.0.0.1:631

---

### Post by sholla on 2008-07-31
Thanks, I now have access to the Printer Configuration panel. 

I have tried printing a test page from there, and even manually installing the printer, all to no avail -  the printer is still not printing. The status of the print job reads - completed.

Pls, what next?:confused:

---

### Post by kimikrishna on 2009-01-07
> $ sudo apt-get install build-essential
$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
$ tar -zxvf foo2zjs.tar.gz
$ cd foo2zjs
$ sudo make uninstall
$ make
$ ./getweb 1020
$ sudo make install install-hotplug

enter this one by one, in terminal [applications > accessories > terminal]

Hope this helps you./

---

