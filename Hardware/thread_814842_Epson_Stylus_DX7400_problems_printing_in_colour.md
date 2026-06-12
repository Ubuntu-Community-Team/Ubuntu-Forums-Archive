---
title: "Epson Stylus DX7400: problems printing in colour"
date: 2008-06-01
forum: Hardware
---

### Post by FSHero on 2008-06-01
I have a problem with my Epson Stylus DX7400 printer. I am using Kubuntu Gutsy (7.10) amd64. When installing my printer using K Menu --> System Settings --> Printers --> Add --> Add printer/class, I could not see my printer in the list. However, I decided to try the Epson DX4800 driver, thinking that it is the most recent printer listed!

For reference: in the Printer settings, the following details are listed under driver details (Properties tab --> Driver on LHS):
Manufacturer: Epson
Printer model: Eps.S. DX4800 gutenpr.-ijs.5.0
Driver info: Epson Stylus DX4800 Foomatic/gutenprint-ijs.5.0

This worked to a limited extent; the black and white output is fine. However, the colour output is slightly incorrect. When I print a printer test page, the colours on the left-hand "colour-wheel" are not continuous; rather, each colour has a gradient. I know that this is not supposed to happen, as I used to have an HP Deskjet 950C whose colour output was a single colour for each of the colours on the "colour wheel" (R K Y M C W B G). I have facetiously scanned with the printer's built in scanner the printout of the test page!
Files:
printer-test-page-epsonstylusdx7400-gutsy.jpg (full page)
colour-wheel-epson.png (losslessly-compressed picture of the colour wheel)

The colour problem also occurs with other documents, e.g. those printed from Firefox or OpenOffice.org. However, there are absolutely no colour problems whatsoever when printing from Windows Vista, using the Epson drivers that are on the driver CD that came with the printer.

Hence... how can I fix this problem to get colour output back to normal?

I would have thought that using the "official" DX7400 driver from Epson's website would solve the problem, but I have not been able to install it successfully. I have tried to compile the driver from their website ([http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) then go to the "Image Scan! for Linux & Photo Image Print System Lite" option and click on the option: Epson Stylus CX7300/CX7400/DX7400). Running ./configure seems to be fine, but when I run make, it seems to fail. I have attached the console output as a text file. File:
compile-error-pipslite.txt

(Please note: I don't have any prior compiling experience; it was really just 'type and pray' for me!)

Thanks to everyone in advance!

---

### Post by teaker1s on 2008-10-26
download alien
```
sudo apt-get install alien
```
download rpm file from avasys site
```
sudo alien di nameofpackage.rpm
```
converts and installs from rpm to deb

---

