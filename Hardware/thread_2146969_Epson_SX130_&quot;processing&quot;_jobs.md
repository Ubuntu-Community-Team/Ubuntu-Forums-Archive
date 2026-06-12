---
title: "Epson SX130 &quot;processing&quot; jobs"
date: 2013-05-20
forum: Hardware
---

### Post by Marzian on 2013-05-20
Hello,
I'm using Ubuntu 13.04 and an Epson SX 130 printer. I don't know exactly how, but after stopping a printing process now it's not printing anymore, not even the test page.

I already tried deleting the printer and install again. It is set as enabled and "accepting jobs". The jobs queue is empty, even in localhost:631, and whenever I add a new job, it just stays as "processing". 

Using another computer (with the latest Lubuntu - where it also worked earlier - doesn't make any difference).

I also tried restarting the printer and unplugging/plugging it again...

Could you help me?

---

### Post by Marzian on 2013-06-02
Please?

Still not working.

---

### Post by pdc on 2013-06-02
I am not sure which driver you are using; 

Epson provide drivers

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16845&DSCCHK=2a380828f942094ec7feca30171d61cb4cdd33e1](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16845&DSCCHK=2a380828f942094ec7feca30171d61cb4cdd33e1)

you would need the epson-inkjet-printer-201101w_1.0.0-1lsb3.2_i386.deb or the epson-inkjet-printer-201101w_1.0.0-1lsb3.2_amd64.deb

if you copy and paste this command

> sudo dpkg -l | grep epson-inkjet-printer into a terminal and copy and paste back what you get......so we can see if they are already installed...........

and if you also paste this

[http://localhost:631/printers/](http://localhost:631/printers/)

into a spare browser window, it allows you to see what cups knows about your system........are any Epson drivers installed there?

---

### Post by Marzian on 2013-06-09
Thanks for the reply!

I installed the i386.deb package and now the command gives back:

> ii  epson-inkjet-printer-201101w         1.0.0-1lsb3.2                       i386         EPSON Stylus NX130 Series - Epson Inkjet Printer Driver
(Earlier it was empty)

While in [http://localhost:631/printers/](http://localhost:631/printers/) I see:

> EPSON-Epson-Stylus-SX130	EPSON Epson Stylus SX130	francesco-desktop	Epson Stylus SX130 Series - epson-inkjet-printer 1.0.0-1lsb3.2 (Seiko Epson Corporation LSB 3.2)	Processing - "Sending data to printer."

But... Even after re-installing the printer from scratch, the test page (or anything else) just stays as "pending"

---

