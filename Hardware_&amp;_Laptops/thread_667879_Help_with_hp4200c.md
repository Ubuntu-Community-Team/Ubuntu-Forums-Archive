---
title: "Help with hp4200c"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by skaramanger on 2008-01-14
Greetings,
I have a HP4200c that is detected correctly by:

terryg@tzdesktop:~$ scanimage -L
device `hp4200:libusb:001:008' is a Hewlett-Packard HP-4200 flatbed scanner

and sane-find-scanner:

found USB scanner (vendor=0x03f0, product=0x0105, chip=PV8630/LM9830) at libusb:001:008

however, gimp give an error popup stating that it failed to open device hp4200:libusb:001:009 invalid argument. xsane or xscanimage just do a core dump. I'm don't know where to find the dump files?

I'm running gutsy 
terryg@tzdesktop:~$ uname -r
2.6.22-14-generic

Any troubleshooting ideas?

Tia,

skaramanger

---

### Post by skaramanger on 2008-01-19
No takers.  I've looked through sourceforge.net w/o seeing a solution.  Maybe I missed something.

Skaramanger

---

### Post by munro on 2008-01-22
I'm having the same problem with my HP C4210. Printer works fine, but SANE won't use my scanner. It finds it, but when I open the scan app, no devices found. I found the hp4200 files on sourceforge, installed them, updated sane, but nothing. I'm thinking that KDE will support it, but I don't know... I like GNOME too much. Any ideas?

---

### Post by skaramanger on 2008-01-31
I don't know much about scanners.  When you power it up does the scanner actually do anything? e.g. self test.  Mine is just recognized.

---

