---
title: "print pdf"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by mangsman on 2006-10-22
I have an hp 1315 and I added the printer successfully as well as installing the hplip driver. I can print everything except for pdfs. What might be the the problem?

---

### Post by dbott67 on 2006-10-22
In OpenOffice, there is a command in the File menu 'Export as PDF'.  For other applications, you will need to do the following:

1. Install cups-pdf
```
sudo apt-get install cups-pdf
```
2. A hack to allow Dapper to create PDF Printer (from [here]("https://launchpad.net/distros/ubuntu/+source/cups-pdf/+bug/42147"))
```
sudo chmod +s /usr/lib/cups/backend/cups-pdf
```
3. Configure CUPS for the PDF printer.
  - Select SYSTEM > ADMINISTRATION > PRINTERS > NEW PRINTER
  - Select LOCAL PRINTER
  - Use detected printer: PDF PRINTER
  - Select Print Driver: 
    - Manufacturer: Generic
    - Model: Postscript Color Printer
    - Name: **postscript-color-printer-rev3b**
  - Click APPLY
4. When printing from any application, select the newly created **postscript-color-printer-rev3b** printer to generate PDF files.

Output files are stored in your home directory under /PDF subirectory.

-Dave

---

### Post by mangsman on 2006-10-23
Does this allow you to print things that you are viewing from say Acroread, or does it allow you to print TO a pdf (export as a pdf)? I'm having the problem that whenever I view something in adobe, when i send it to my printer for printing, nothing happens...

---

### Post by dbott67 on 2006-10-24
I'm sorry, I misunderstood your original problem.  It allows you to export *to* PDF format.

-Dave

---

### Post by bodycoach2 on 2006-10-24
Thanks for those instructions. I tried to instructions in the Ubuntu Hacks book, but I think it was incomplete. These instructions worked. Getting much closer to paperless office!

> **dbott67 said:**
> In OpenOffice, there is a command in the File menu 'Export as PDF'.  For other applications, you will need to do the following:

1. Install cups-pdf
```
sudo apt-get install cups-pdf
```
2. A hack to allow Dapper to create PDF Printer (from [here]("https://launchpad.net/distros/ubuntu/+source/cups-pdf/+bug/42147"))
```
sudo chmod +s /usr/lib/cups/backend/cups-pdf
```
3. Configure CUPS for the PDF printer.
  - Select SYSTEM > ADMINISTRATION > PRINTERS > NEW PRINTER
  - Select LOCAL PRINTER
  - Use detected printer: PDF PRINTER
  - Select Print Driver: 
    - Manufacturer: Generic
    - Model: Postscript Color Printer
    - Name: **postscript-color-printer-rev3b**
  - Click APPLY
4. When printing from any application, select the newly created **postscript-color-printer-rev3b** printer to generate PDF files.

Output files are stored in your home directory under /PDF subirectory.

-Dave

---

