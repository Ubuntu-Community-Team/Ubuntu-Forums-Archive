---
title: "HP Printers?"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by computerguy867 on 2005-03-14
Is there any way to install HPLIP.  I tried following the exact instructions on HP's site and got:

make[3]: *** [install-foomatic] Error 2
make[3]: Leaving directory `/home/computerguy867/hplip-0.8.8/prnt/hpijs'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/computerguy867/hplip-0.8.8/prnt/hpijs'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/computerguy867/hplip-0.8.8/prnt/hpijs'
make: *** [install-recursive] Error 1

after make install

Im new to linux so im not sure whats causing this.  Also, as a side note, will HPLIP be in the Hoary library?

---

### Post by macewan on 2005-03-14
[QUOTE=computerguy867]Is there any way to install HPLIP.  I tried following the exact instructions on HP's site and got:

make[3]: *** [install-foomatic] Error 2
make[3]: Leaving directory `/home/computerguy867/hplip-0.8.8/prnt/hpijs'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/computerguy867/hplip-0.8.8/prnt/hpijs'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/computerguy867/hplip-0.8.8/prnt/hpijs'
make: *** [install-recursive] Error 1

after make install

Im new to linux so im not sure whats causing this.  Also, as a side note, will HPLIP be in the Hoary library?[/QUOTE]
 What printer

---

### Post by computerguy867 on 2005-03-14
Its an Officejet 4215.  Also, how does the multi functioning (scan/fax/printer) work in linux.

---

### Post by computerguy867 on 2005-03-15
Anyone?

---

### Post by macewan on 2005-03-16
[QUOTE=computerguy867]Anyone?[/QUOTE]
 [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_4200](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_4200)

---

### Post by kleeman on 2005-03-16
I tried to get it (hplip) working without success as well (on warty). It tries to overwrite some other packages as best I could work out. Best avoided until it is incorporated into the distro unless you want to bork packages  :)

---

