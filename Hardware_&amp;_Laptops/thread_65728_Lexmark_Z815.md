---
title: "Lexmark Z815"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by mojo_risin on 2005-09-14
Hi,

There is any support for the 810 series?
I didn't found nothing :(
It would be cool if I could use my printer on Linux.

Paulo

---

### Post by mojo_risin on 2005-09-16
I found this page: [http://cerqueira.org/software/z810/](http://cerqueira.org/software/z810/)
but it points to the           
Lexmark Linux Printer Driver Developer's Kit and not the driver itself, so nothing done :(

---

### Post by assan on 2005-10-25
try this wiki page: [https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ810](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ810)

---

### Post by ptike on 2005-11-08
hello

I tryed the wiki page for the lexmark z810, but I got the following error while compiling

root@hawk:/home/ptike/z810/Z810CUPS-0.7 # make rpm-compat
root@hawk:/home/ptike/z810/Z810CUPS-0.7 # make
(cd ./source/backend; make -f Makefile)
make[1]: Entering directory `/home/ptike/z810/Z810CUPS-0.7/source/backend'
make[1]: `../../bin/z810' is up to date.
make[1]: Leaving directory `/home/ptike/z810/Z810CUPS-0.7/source/backend'
(cd ./source/filter; make -f Makefile)
make[1]: Entering directory `/home/ptike/z810/Z810CUPS-0.7/source/filter'
[ -d Objects ] || mkdir Objects
g++  -I./ -c -g -Wall -O2 -funsigned-char main.cpp -o Objects/main.o
In bestand ingevoegd door z810filter.h:30,
                 door main.cpp:33:
cupsraster.h:24:25: fout: cups/raster.h: Onbekend bestand of map
cupsraster.h:117: fout: ISO C++ forbids declaration of ‘cups_raster_t’ with no type
cupsraster.h:117: fout: expected ‘;’ before ‘*’ token
cupsraster.h:118: fout: ‘cups_page_header_t’ does not name a type
make[1]: *** [Objects/main.o] Fout 1
make[1]: Leaving directory `/home/ptike/z810/Z810CUPS-0.7/source/filter'
make: *** [all] Fout 2

Anybody an idea what to do?

thx

---

### Post by wwitthoff1 on 2006-04-25
I got the same problem but installed the package libcupsimageimage2-dev and it compiled fine.

---

### Post by tomer85 on 2007-02-12
Hi

I'm searching for lexmark z810 driver. When i google i get a link to [http://cerqueira.org/software/z810/](http://cerqueira.org/software/z810/) ,but this page doesn't exist. Can somebody send me this file ?

---

### Post by fufi_ on 2007-02-15
I need this file too!

Can anybody send me this file?

---

### Post by phaedrus44 on 2007-03-15
hello..

i also need this driver!    so so so close

i have a lexmark z816  this would be perfect

please email me if anyone has it   [email]michaelshiltz@hotmail.com[/email]

thanks you!:guitar:

---

### Post by dazer26 on 2007-05-08
I got up to installation then I get this error...

mike@Xblade:~$ tar -zxvf Z810CUPS-0.7.1.tar.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors
mike@Xblade:~$ tar -zxvf Z810CUPS-0.7.tar.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors

As you can see I tried with both the old and new version.  Any ideas?  Has anyone actually gotten this printer to work on ubuntu??
...I knew I shoulda stuck with HP....

---

### Post by raphenry on 2007-07-13
[COLOR="Navy"]I also got this for a response when i tried to expand the file, it does not appear to be a tar achive[/COLOR]

virtual-raphael.OG6J1O
Z810CUPS-0.7.1.tar.gz
Z810_Printer_Specific_Interface_to_LLPDDK_(v20).pdf
zmanReAKq8
raphael@family-desktop:/tmp$ tar -zxvf Z810CUPS-0.7.1.tar.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors
raphael@family-desktop:/tmp$ 

[COLOR="Navy"]would really appreciate some help, tried to contact the WIKI writer, but could not. 

Thanks for your help and patience, one of the newbies [/COLOR]:confused:

---

### Post by g2g591 on 2007-08-14
if you guys still havn't got it to work see [http://ubuntuforums.org/showthread.php?t=505886&highlight=z810](http://ubuntuforums.org/showthread.php?t=505886&highlight=z810)

---

