---
title: "Help with HP Deskjet 5740 printer and Epson Perfection 1260 Scanner"
date: 2005-12-24
forum: Hardware &amp; Laptops
---

### Post by skjantzen on 2005-12-24
I can't get either of these two devices to work with my new Ubuntu install. Any help would be appreciated. 

scott

---

### Post by anil_robo on 2005-12-25
Installation instructins for your printer: HP DeskJet 5740
[http://hpinkjet.sourceforge.net/install.php#HPLIP]("http://hpinkjet.sourceforge.net/install.php#HPLIP")
I believe you're using Ubuntu, so you'll follow the Debian distribution instructions.
After you've enabled your printer, please post your experience here, so that others can benefit too!
Merry Christmas! :)

---

### Post by anil_robo on 2005-12-25
Your scanner drivers (Epson Perfection 1260 scanner):
[http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=News&oid=14553&prodoid=21643923&noteoid=38581](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=News&oid=14553&prodoid=21643923&noteoid=38581)
Your drivers are not on that page, but you'll have to go to the Epson Kowa website (link given on the above page I mentioned).

After you've enabled your scanner, please post your experiences here so as to benefit others. THanks. :)

---

### Post by skjantzen on 2005-12-26
Thanks for the info on downloading iscan from the Epson website. The only two formats are .rpm and source (.tar.gz). I downloaded the .tar.gz version but when I did ./configure I got the following:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

Any suggestions as to what is going wrong?

Thanks,

scott

---

