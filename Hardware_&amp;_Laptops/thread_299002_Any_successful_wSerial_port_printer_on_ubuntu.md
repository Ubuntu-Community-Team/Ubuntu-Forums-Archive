---
title: "Any successful w/Serial port printer on ubuntu?"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by bobmct on 2006-11-13
:confused: 
Gentlemen;
Have any of the readers ever actually sucessfully installed onto an x86 ubuntu system a serially attached printer AND have it work well (or at all)???

I've been playing with one for about 3 weeks and while I can cat a file to it the printout takes approx 10 minutes for a three short line output.  I verified the serial port assignment by viewing dmesg|grep serial and its assiged as /dev/ttyS2 and I've used setserial to set the port params to those of the printer (9600/8/n/1/xonxoff) but I cannot get any further.  I can assign the printer in cups but even cups outputs with the same turtle-slow speed.

Any ideas?  Clues?  

And I know I should be using other printer interfaces but this is application specific (unique label/receipt printers).

bobmct

---

### Post by edemark on 2006-11-14
have you tried to set up your printer via lpd. 
[http://tldp.org/HOWTO/Printing-HOWTO/serial.html](http://tldp.org/HOWTO/Printing-HOWTO/serial.html)

hope it helps

---

### Post by bobmct on 2006-11-16
Yes, in fact, that's the ONLY way I can set it up.  And I can direct output to it from my program (pipe through to lp) and use cups to view the job queue but the printer either doesn't move or moves at the rate of approx 1 line per 15 minutes.  ](*,)

---

### Post by SonWon on 2006-11-16
If I had to guess it sounds like some kind of odd handshaking problem between the computer and the printer.  Are you sure you have the correct cable?

I haven't actually done this with Linux so this is a wild guess on my part.

SonWon

---

