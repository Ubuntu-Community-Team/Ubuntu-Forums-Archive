---
title: "Xerox FX Apeos Port -II C4300 Printer Driver"
date: 2010-02-01
forum: Hardware
---

### Post by Martin Lam on 2010-02-01
Hi,

I have tried this:

[http://download.fujixerox.co.jp/apeosport/download/c4300series/linux/index.html](http://download.fujixerox.co.jp/apeosport/download/c4300series/linux/index.html)

but still had no luck on making it work.  Does anyone have successful experience on using "fxlinuxprint.ppd"?  

Thanks in advance!

Martin

---

### Post by ethoms on 2010-07-16
I have almost exhausted attempts to get Fuji Xerox DocuCentre-II C3000 (AKA ApeosPort-II C3000)to work under linux CUPS. I have contacted Fuji Xerox and they contacted tech departments in other countries. Bottom line is it won't work without the PostScript Kit (hardware extra).

If anyone can prove them wrong, I would love to know.

---

### Post by rockdj on 2010-08-09
I'm currently using that driver on Ubuntu 10.04 (32-bit) and able to print successfully to our C4300 MFD.  The only thing I'm trying to troubleshoot atm about this is printing multiple copies.  

At any rate, I downloaded the RPM from the FujiXerox Japanese site -- [http://download.fujixerox.co.jp/pub/exe/apeosport/c4300series/fxlinuxprint-1.0.1-1.i386.rpm](http://download.fujixerox.co.jp/pub/exe/apeosport/c4300series/fxlinuxprint-1.0.1-1.i386.rpm) and then extracted the contents thusly:   

[LIST]
[*]In the RPM, I extracted the PPD file at ./usr/share/cups/model/FujiXerox/en/fxlinuxprint.ppd and selected this file when asked to "Provide PPD file" when selecting a print driver.
[*]The driver complained about you missing certain programs (eg pdftopdffx, pdftopjlfx and/or pstopdffx). These are located in the above RPM file, in ./usr/lib/cups/filter/. I put these files into the same location on your hard drive (root/sudo access required), and the driver found them.
[/LIST]

And then just added a printer normally in Ubuntu, selecting the relevant PPD file in the process.

---

### Post by diagonallemma on 2010-09-01
Thanks rockdj, this way I finally managed to print on our DocuCentre II 3005. Just a small addition: I had to chown root:root the files copied to /usr/lib/cups/filter/, otherwise I received a "scheduler could not execute a filter" error.

---

### Post by myqlarson on 2010-11-30
Thanks, it worked for me to. I had to convert the RPM to DEB with Alien, which threw an error but otherwise completed successfully.

---

