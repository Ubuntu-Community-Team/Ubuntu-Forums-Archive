---
title: "Epson Stylus CX7400 scanner"
date: 2009-04-30
forum: Hardware
---

### Post by enduser000 on 2009-04-30
I'm happy to say that the printing works out of the box on this printer (Stylus CX7400) in 9.04 for me.  I would like the scanner to work though.  When I go to xsane though, it says: "Failed to open device `v4l:dev/video0': Invalid argument".

Does anyone know what this means or how to fix it? Thanks for taking a look,

enduser

---

### Post by chudder on 2009-05-08
Exact Same problem here with a Epson Stylus NX100

---

### Post by enduser000 on 2009-05-13
Anyone know what the problem is?  It would be nice not to have to boot into windows just to scan a paper or drawing,

enduser

---

### Post by chudder on 2009-05-16
I agree.  I tried installing the iscan package which you can get from xsane website but still no scanner :(

---

### Post by Andrew_Grant on 2009-05-16
See this thread: [http://ubuntuforums.org/showthread.php?t=1037527&highlight=xsane](http://ubuntuforums.org/showthread.php?t=1037527&highlight=xsane)
Quick points:
1:the ID for an Epson CX7400 is 0x4b8 0x838
2:when xsane starts make sure you select the first scanner highlighted (usually the default, but not always)
and
3:the colour settings are usually set to binary. click the panel and change to colour,

---

### Post by erikthedrink on 2010-04-01
I also have an Epson CX7400, and the printing part works fine.  I downloaded and installed XSANE.  My printer is detected as online.  When I run XSANE, I get this message "no devices available."  I have Ubuntu 9.10 GNOME.

---

### Post by ellgor on 2010-04-02
Hi,

Try running xsane from a terminal :

sudo xsane

or if you have Imagescan

sudo imagescan

seems to be a permission issue, Imagescan normally needs a reboot to get it stated properly.

Regards, Ellgor.

---

### Post by sisco311 on 2010-04-02
> **erikthedrink said:**
> I also have an Epson CX7400, and the printing part works fine.  I downloaded and installed XSANE.  My printer is detected as online.  When I run XSANE, I get this message "no devices available."  I have Ubuntu 9.10 GNOME.

You have to install iscan, then it will work with xsane too.

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

---

### Post by erikthedrink on 2010-04-02
I tried running the .deb version of the package file -- I got this message
Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)

I could not find libltdl3 in the synaptic package manager.

---

### Post by sisco311 on 2010-04-03
> **erikthedrink said:**
> I tried running the .deb version of the package file -- I got this message
Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)

I could not find libltdl3 in the synaptic package manager.

you have to download & install iscan_2.24.0-4.ltdl7_i386.deb

---

### Post by erikthedrink on 2010-04-03
Where is this iscan file.  After I fill out the information on the link you gave me, I get only this deb file
pipslite_1.4.0-5_i386.deb
Provide the specific link, please.  And then, I get the aforementioned lib3 error.

---

### Post by erikthedrink on 2011-01-24
I did a fresh install with Ubuntu 10.10, Maverick Meerkat, from the Ubuntu website.  Without tinkering, the Simple Scan program works with the CX7400.:KS

---

