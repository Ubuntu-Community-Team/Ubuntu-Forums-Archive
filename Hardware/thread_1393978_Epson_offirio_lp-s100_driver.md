---
title: "Epson offirio lp-s100 driver?"
date: 2010-01-30
forum: Hardware
---

### Post by tora201 on 2010-01-30
Does anybody know if this printer works?

[http://www.epson.jp/products/offirio/printer/lps100/](http://www.epson.jp/products/offirio/printer/lps100/)

Silly me, after my Brother 2040 died I went and got the above printer (works fine with my MAC/Windows 7, but no Linux driver that I can find.

Of course, I have tried other LP drivers through CUPS, but to no avail.

Is it possible to use the PPD from either the Windows driver or Mac version?

Anybody have any ideas/hints? Cheers.

EDIT: solved - See post 5

---

### Post by tora201 on 2010-01-31
Bump? Probably nobody has even heard of a similar printer.... I guess I am all alone here....

---

### Post by ellgor on 2010-01-31
Hi,

Go to the "Avasys" site, its for Epsons, they might have what you need.

Regards, Ellgor.

---

### Post by ellgor on 2010-01-31
Hi,

Go to the "Avasys" site, its for Epsons, they might have what you need.

Regards, Ellgor.

---

### Post by tora201 on 2010-02-02
Thanks mate - i have tried that. Don't have my model. Perhaps it takes a few months for them to incorporate a new model into their driver? (mine came out in Sep last year in Japan, I think). I see the lp-s300 is included but does not work with mine. Cheers!

---

### Post by tora201 on 2010-03-17
If anybody else ever happens to have problems using this printer in Ubuntu/linux, I have solved it! Go here and follow instructions:

[http://ubuntuforums.org/showthread.php?t=696363&highlight=6200l](http://ubuntuforums.org/showthread.php?t=696363&highlight=6200l)

After some research, I discovered the lp-s100 is in fact known as an EPL-6200L (not to be confused with the EPL-6200!).

Anyway, all going now. :D

---

### Post by hkubun on 2013-01-20
Hi! I use Epson offirio lp-s 100 .
My version is the ubuntu 12.04.
I print the printer test page of ubuntu and some Web pages of firefox.
Driver: EPL6200L.PPD
Make and Model: Epson EPL-6200L Foomatic/epl6200l (recommended)
Printer: EPSON-LP-S100
EPL-6200L-Hardy.ppd was copied into /usr/share/cups/model/epson_ppd directory.
epsoneplijs-0.4.1.tgz was extracted and done by next commands.
./cofigure --prefix=/usr 
make
sudo make install
:D very happy.

---

