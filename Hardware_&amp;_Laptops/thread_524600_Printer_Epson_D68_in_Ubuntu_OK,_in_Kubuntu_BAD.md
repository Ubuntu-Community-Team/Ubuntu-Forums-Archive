---
title: "Printer Epson D68 in Ubuntu OK, in Kubuntu BAD"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by gaiterin on 2007-08-13
Hi.
My Ubuntu 7.04 works perfect with Epson D68 Printer (it appear in the printer's list when add a new printer).
But I now install Kubuntu 7.04 and Kubuntu doesn't know wich driver much be used!
Thanks

---

### Post by 1/0 on 2007-08-13
Well... 

I don't know how to put this the easiest way, since we're completely different kind of users. According to [http://openprinting.org](http://openprinting.org) your printer is supported via the Lexmark z600 driver. Ref. [http://openprinting.org/show_printer.cgi?recnum=Epson-d68](http://openprinting.org/show_printer.cgi?recnum=Epson-d68)

I am, however, able to find your printer in the list of printers in Cups. Have you configured your printer according to the [ubuntuguide?]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") You need foomatic installed. Just check in a browser on localhost:631

---

### Post by gaiterin on 2007-08-13
I solved it as:
First "sudo passwd root" in a console, follow the dialogue and make a root password.
And go to:
[http://localhost:631/admin](http://localhost:631/admin)
The printer appear :)

Thanks

---

