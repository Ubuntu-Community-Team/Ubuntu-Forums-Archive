---
title: "My Ubuntu Woes on a Acer Aspire 1694WLMi"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by Pnin on 2006-06-30
I have a Ubuntu 5.10 Breezy DVD which was published by Linux Magazine 63, back in February. I have installed it several times in my Acer Aspire 1694 Laptop with the same discouraging results.

The reason I chose to stay with a superseded version is that, after much forum/wiki/docs browsing/reading, I concluded that it was better suited to my newbie needs. I seem to be at a dead end, so I decided to post here, hoping someone will have a remedy.

- xorg.conf needs to be edited for the display to work; (solved)
- ACPI doesn't work;

I tried to follow the steps outlined here
[https://wiki.ubuntu.com/Ubuntu5.10OnAcerAspire1692WLMi](https://wiki.ubuntu.com/Ubuntu5.10OnAcerAspire1692WLMi), but after succeeding to install gcc and getting make to work -- my luck for having an install DVD filled with the packages I would otherwise have to download from the Net -- I was unable to figure what went wrong with the compilation of the ACPI CA refered to in point 3 -- see below:

*****@***********:~/acpica-unix-20060608/compiler$ make
bison -v -d -y -pAslCompiler aslcompiler.y
aslcompiler.y:3076.37-48: warning: rule never reduced because of conflicts: OptionalResourceType: /* empty */
cp y.tab.c aslcompilerparse.c
cp y.tab.h aslcompiler.y.h
cc -Wall -O2 -Wstrict-prototypes -D_LINUX -DACPI_ASL_COMPILER -I../include    -c -o aslcompilerparse.o aslcompilerparse.c
flex -i -PAslCompiler -oaslcompilerlex.c aslcompiler.l
cc -Wall -O2 -Wstrict-prototypes -D_LINUX -DACPI_ASL_COMPILER -I../include    -c -o aslcompilerlex.o aslcompilerlex.c
aslcompiler.l: In function â€˜commentâ€™:
aslcompiler.l:847: error: â€˜yytext_ptrâ€™ undeclared (first use in this function)
aslcompiler.l:847: error: (Each undeclared identifier is reported only once
aslcompiler.l:847: error: for each function it appears in.)
make: *** [aslcompilerlex.o] Error 1

- batery indicator doesn't work.
I am sure this one is due to the ACPI problem.

- network doesn't work.
I guess it has do to with ACPI being disabled, since I have had to add acpi=off noapic to grub menu options. I have tried both DHCP and a fixed IP to no avail. The network configuration panel shows the adapter as being active, everything seems operational, but I can not ping any ip. See attached lscpi, lsmod and lshw output for more info.

Any help appreciated since I seem to be going nowhere. #-o

Pnin

---

### Post by leo-pold on 2006-07-05
Webmaster.
Increase yor traff :
Add your link free :
[http://www.price-rx.net](http://www.price-rx.net)
[http://www.shoppingnets.net](http://www.shoppingnets.net)
[http://www.medication-online.net](http://www.medication-online.net)
[http://www.freedoms-pharmacy.com](http://www.freedoms-pharmacy.com)
[http://www.freedom-pharmacys.com](http://www.freedom-pharmacys.com)
[http://www.online-pharmacys.net](http://www.online-pharmacys.net)
[http://www.drugs-purchase.com](http://www.drugs-purchase.com)
[http://www.drugs-sale.com](http://www.drugs-sale.com)
[http://www.drug-shopping.com](http://www.drug-shopping.com)
[http://www.free-rx-drugstore.com](http://www.free-rx-drugstore.com)
[http://www.brand-store.org](http://www.brand-store.org)
[http://www.health-beauty-product.com](http://www.health-beauty-product.com)
[http://www.american-pharmacys.com](http://www.american-pharmacys.com)
[http://www.noblechemist.net](http://www.noblechemist.net)
[http://www.noble-chemist.com](http://www.noble-chemist.com)
[http://www.safe-pharmacy.com](http://www.safe-pharmacy.com)
[http://www.fda-drug.com](http://www.fda-drug.com)
[http://www.shoe-buy.net](http://www.shoe-buy.net)
[http://www.shoes-warehouse.net](http://www.shoes-warehouse.net)
[http://www.store-rx.net](http://www.store-rx.net)
[http://www.lifes-style.com](http://www.lifes-style.com)
[http://www.freedom-rx.com](http://www.freedom-rx.com)
[http://www.rx-list.net](http://www.rx-list.net)

---

### Post by Pnin on 2006-07-07
Great! Not only I got not even a single answer, but my thread has been spammed. I doesn't get better than this... ](*,)

---

### Post by Pnin on 2006-07-10
OK, I get it. I'll try Suse...

---

