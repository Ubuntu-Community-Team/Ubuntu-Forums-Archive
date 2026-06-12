---
title: "Has anybody used scanbuttond with an HP printer?"
date: 2010-01-29
forum: Hardware
---

### Post by Fitch on 2010-01-29
This is a "sort of" hardware question in that the Hewlet Packard PSC1350 All-in-1 scanner printer is not supported in scanbuttond

The HPLIP application does very well, except for the button push on the printer. HPLIP cannot see and probably never will see a scan request from the printer.

But scanbuttond might!

I downloaded the tar and altered the epson .c ('cos I don't know enough to make a new HP.c) by adding 03f0, 3b11, 1  HP PSC 1350 in the right place, added 1 to the number of "epson" devices, and make installed.  

Scanbuttond sees it fine, but doesn't do anything.

Have I missed something?

---

### Post by steveneddy on 2010-01-29
Is your all-in-one attached to the USB port or the Ethernet cable?

---

### Post by Fitch on 2010-01-29
Oops I'm being mean with information  (I'm not quite sure what info people need normally) Sorry! 

It's connected to the USB port.

---

### Post by Fitch on 2010-03-20
bump

---

### Post by nik_nah on 2010-06-01
I had been using scanbuttond but it always had problems, sometimes it'd detect the button and sometimes not, and after a few ubuntu upgrades it just stopped working.

Can you see the printer's scanner if you run "scanimage -L" under root?

If you can then try out a patched version of something that I found in another package "scanmonitord".  I've put it here...

[http://dunno.com/src/scanmonitord-sanebd.tar.bz2](http://dunno.com/src/scanmonitord-sanebd.tar.bz2)

It simply runs /etc/scanbuttond/buttonpressed.sh  whenever a button is pressed.

---

### Post by Fitch on 2010-06-17
Lucid kicks it out
Don't worry. This is the last time I will be posting as I've gone back to Windows.

---

