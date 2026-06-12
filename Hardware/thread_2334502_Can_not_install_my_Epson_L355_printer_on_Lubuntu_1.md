---
title: "Can not install my Epson L355 printer on Lubuntu 16.04"
date: 2016-08-20
forum: Hardware
---

### Post by johannio2 on 2016-08-20
I have installed Lubuntu 16.04 and can not install my Epson printer L355, basically I tried two ways:

1. Downloaded from [www.openprinting.org]("http://www.openprinting.org") and installed the package: epson-inkjet-printer-201207w_1.0.0-1lsb3.2_i386.deb. Apparently it installed fine but when opening "Printers" window, although it appears "connected to localhost" there is a message "there are not printers configured yet" and pressing the "add" button it asks for an "URI code", for me it does not look as the right path. In fact, this PC ran on Lubuntu 14.04 for two years and at that time it was pretty easy to configure just the same printer.

2. Using the terminal I have installed "cups-2.2rc1" package. Then tried the browser to go to "http://localhost:631" and the answer was: "can not connect"

Two more details: One, before step 1 using the terminal I installed the LSB3.2 package, and two: it is not a hardware issue, in fact I can scan without problem with "Simple Scan" and as I mentioned it worked fine on Lubuntu 14.04.

My wife and I will be very grateful of your help as we depend on printing for our daily work.

Greetings and thanks

---

### Post by Mark Phelps on 2016-08-20
It's localhost:631 -- not 613.

---

### Post by johannio2 on 2016-08-20
You are right!. I am sorry, I meant [COLOR=#000000] localhost:631 (not 613). It was a typing mistake. I[/COLOR] will edit it right away... Thanks!

---

