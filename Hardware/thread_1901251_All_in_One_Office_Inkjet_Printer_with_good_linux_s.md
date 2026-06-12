---
title: "All in One Office Inkjet Printer with good linux support"
date: 2011-12-28
forum: Hardware
---

### Post by heito on 2011-12-28
I am looking for an all in one office inkjet printer with good 64 bit linux support. I have already a shortlist of printers and I am looking for user experiences with those printers under linux (64 bit). Expercially I want to know the follwing:

1. Does printing work as well as under windows (speed, quality)
2. Does scanning work as well as under windows
3. Does the fax function work
4. How stable are the linux drivers
5. Any drawbacks in comparison with the windows drivers
6. Does the WLAN and LAN ports of those printers work under linux?

Here is my printer shortlist:

- [Epson Stylus Office BX635FWD]("http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-Stylus-Office-BX635FWD")
- [Epson Stylus Office BX535WD]("http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-Stylus-Office-BX535WD")
- [Epson WorkForce Pro WP-4525 DNF]("http://www.epson.co.uk/Store/Printers-and-All-in-Ones/Epson-WorkForce-Pro-WP-4525-DNF")
- [HP Officejet Pro 8600 e-All-in-One Printer]("http://www.shopping.hp.com/store/product/product_detail/CM749A%2523B1H")

---

### Post by Paddy Landau on 2011-12-28
HP has an excellent history of supporting Linux (you have to install [hplip]("apt:hplip"), available from the repositories).

I have used a couple of HP printers; my current one is an HP OfficeJet Pro L7780, and I have been extremely happy with it.

I don't know if the fax works, as I don't use fax at all, but the other functions -- photocopying, scanning directly to computer, printing -- work perfectly with both Windows 7 and Linux Ubuntu 11.04. (You need Samba working for scanning to work with Ubuntu.)

---

### Post by pcolamar on 2011-12-28
Be careful with HP though.
I have a 6450 in the office that works very well with Ubuntu so I bought a year later a 6500A for home.
Bad choice, I have never got to scan from the feeder no matter what hplip release I install, and it's 9 months now.
Worst, I read in a forum a thread a year that HP knows of the problem but.... I have installed already 5 updated versions of HPlip and none corrects the problem.

---EDIT Jan2012 ---
Just a due update.

At the 6th HPlip update (ver. 3.11.12) , all my problem with the 6500A (710n-z) seems to be solved.

Kudo to HP

---

### Post by heito on 2011-12-28
I don't really need the copy function and don't really need the fax. So it is perhaps a better idea to buy just a good printer such as HP Officejet 8100 Pro and buy a separate scanner in a second step.

---

### Post by Paddy Landau on 2011-12-29
> **heito said:**
> ... perhaps a better idea to buy just a good printer such as HP Officejet 8100 Pro and buy a separate scanner in a second step.
Well, that depends on space and cost. It may be cheaper and take less space to purchase an all-in-one.

---

### Post by colin.p on 2011-12-29
> **pcolamar said:**
> Be careful with HP though.
I have a 6450 in the office that works very well with Ubuntu so I bought a year later a 6500A for home.
Bad choice, I have never got to scan from the feeder no matter what hplip release I install, and it's 9 months now.
Worst, I read in a forum a thread a year that HP knows of the problem but.... I have installed already 5 updated versions of HPlip and none corrects the problem.

I responded in another printer thread awhile ago that someone said basically what you said. However, I have the HP Officejet 6500 wireless printer that all three of my lucid computers print, fax, copy and scan to. However, my printer is connected to a router ethernet port that gives it a static IP.
Don't know if that's the reason or not. The version of HPLIP is the one that came with lucid.

---

### Post by Paddy Landau on 2011-12-30
> **colin.p said:**
> ... my printer is connected to a router ethernet port that gives it a static IP.
That's a good point and one I forgot about. I also give mine a static IP address.

---

### Post by SeijiSensei on 2011-12-30
Just a warning that not all HP scanners have Linux support.  I have a ScanJet 4850 that someone was discarding and discovered it has [no Linux drivers]("http://www.linuxquestions.org/questions/linux-newbie-8/any-distros-that-support-an-hp-scanjet-4850-a-835818/").  It's otherwise a lovely device, but it only works for me in Windows.

Check these pages before making your purchase:

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html) (HP devices)

---

### Post by colin.p on 2011-12-30
I just wanted to add that if the printer is close you may be able to scan, copy and fax direct from the printer console, as a lot of the all in one printers have that. There is usually more than one way to skin a cat.

---

