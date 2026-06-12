---
title: "Noobie Printer Question"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by josesanders on 2006-12-27
I'm fairly new to linux, but I want to use an old PC as a print server on my network, consisting of a few Windows XP and Edgy machines.  I've seen a few threads about how to do this, but I don't totally understand how it works.  My question is, if the server is going to be running windows, do I still need linux drivers for the printers?  This is an important point, as I haven't been able to get either of the two printers to work in Linux.

---

### Post by KenSentMe on 2006-12-27
You still need to install the printer drivers for Linux. 

What printers are you talking about?

---

### Post by josesanders on 2006-12-27
One's an HP Laserjet 4M, and I tried the driver, but it just printed a single blank test page, and then nothing when I try to print from other applications (it works great in Windows, of course).  The other is a Lexmark x3350 all-in-one thing that I just inherited.  I can hope to maybe get the HP to work someday, but I think the Lexmark is probably not even worth my time.  I don't see why it isn't possible for the Ubuntu printing service to just send the print job in some generic format, like PPM or something, to the print server, and then the print server would use the locally installed drivers to print it.

---

### Post by KenSentMe on 2006-12-28
What driver have you tried to get the HP 4M running? Try the hpijs driver, most other printers on this list [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp) work without problems with the hpijs driver.

---

