---
title: "List of all in one printers with support for Ubuntu 11.04"
date: 2011-09-15
forum: Hardware
---

### Post by jockyburns on 2011-09-15
As the title says,,, can anyone suggest an all in one printer/scanner/copier, with good support eg drivers etc designed for Linux operating systems? I'm running Ubuntu 11.04 and am struggling to install my old Lexmark printer X1270. So I'm looking at buying a new AIO printer with support for Linux OS's .

Cheers JB ;););)

---

### Post by gandaran on 2011-09-15
HP printers are the best supported printers for use with Linux

---

### Post by haqking on 2011-09-15
> **jockyburns said:**
> As the title says,,, can anyone suggest an all in one printer/scanner/copier, with good support eg drivers etc designed for Linux operating systems? I'm running Ubuntu 11.04 and am struggling to install my old Lexmark printer X1270. So I'm looking at buying a new AIO printer with support for Linux OS's .

Cheers JB ;););)


This is probably the closest you could get...kind of ;-)

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

and here:

[http://www.linux-drivers.org/printer_scanner.html](http://www.linux-drivers.org/printer_scanner.html)

---

### Post by ibutho on 2011-09-15
HP printers and all in ones are well supported by Linux.

---

### Post by jim_deadlock on 2011-09-15
I have an Epson Stylus SX515W and I can't fault it, works great over wifi and everything. Nice price too.

---

### Post by sammiev on 2011-09-15
Epson has been great for me as well. :)

---

### Post by jockyburns on 2011-09-15
Thanks peeps. HP or Epson it is then. I'll look around for an HP all in one I think as my comp is an HP (well it used to be !!!. The case/dvd rw and cd rw are, but had a new mobo,psu, memory and cpu last year and  a new HDD a few weeks ago. (after HDD failure) Probably unrecognisable from the original now, but at least it works brilliantly)

Thanks again.;););););)

---

### Post by agillator on 2011-09-15
HP printers work flawlessly with Linux - if you install HPLIP! I highly recommend downloading the HPLIP installer from HP, then uninstall the one Ubuntu installs and install the new one. That will give you full use of the scanner through XSane.

I have no experience with Epson - well, not in the last twenty years or so - so can't speak about them.

---

### Post by wildmanne39 on 2011-09-15
+1 for hp mine has never given me any trouble.

---

### Post by gbrowne on 2011-09-27
> **agillator said:**
> HP printers work flawlessly with Linux - if you install HPLIP!

Have to take some issue with that agillator...  I used HPLIP with my wireless HP Photosmart C309a for quite a while and it did work extremely well with all features (double sided/ADF etc) for printing and scanning until suddenly one day it refused to print because I couldn't get it to ignore the (incorrect) messages from the printer saying that the ink cart was empty.  I refill my old carts to save money, but the stupid inbuilt chip still reports empty cart and the HPLIP drivers seem to take that as gospel.

After some googling, I removed HPLIP and can now print to the printer again but using using CUPS, despite the low-ink warnings.  Of course now XSane reports 'No devices available'.  Tried to install libsane-hpaio, but ran into dependancy issues that wanted to reinstall HPLIP.  I have not been able to get round this yet so currently my scanner is unusable.

GB.

---

### Post by rewyllys on 2011-09-27
Brother provides good support for Linux.  FWIW, in Ubuntu 11.04 I'm currently happily using a 6-year-old Brother MFC-8820DN, and I'd think that its currently available successor(s) would work the same way.

---

