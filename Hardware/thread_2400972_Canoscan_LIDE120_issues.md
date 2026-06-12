---
title: "Canoscan LIDE120 issues?"
date: 2018-09-12
forum: Hardware
---

### Post by eezacque on 2018-09-12
Bought a new Canoscan LIDE120 scanner, only to find it impossible to use with the XSane scanning frontend:
- I cannot repeatedly scan without restarting the software after each scan
- I often get a useless blank preview window, without button to acquire preview, which is only solved by removing the preferences file
- I get lots of device IO errors
- I get lots of scans which are either solid black, or partly black, or striped like a barcode
As a result, it sometimes takes me as long as 10 minutes to get one decent scan.

I am trying to find out whether it's the scanner, or the software used, that causes these problems.
Is there anything I can do to sort this out, other than sending the scanner back and getting a replacement?

---

### Post by him610 on 2018-09-12
eezaque,

From the command line, post the results of *scanimage -L*

---

### Post by eezacque on 2018-09-13
> **him610 said:**
> eezaque,

From the command line, post the results of *scanimage -L*

$ scanimage -L
device `genesys:libusb:003:022' is a Canon LiDE 120 flatbed scanner

---

### Post by him610 on 2018-09-14
Well, that shows your scanner is recognized by your system, and I would think it is not hardware. It could be that the incorrect driver is installed. 
I use Simple Scan for my two scanners. I might add that I have never encountered any problems with either my Epson Perfection 1640 (USB) nor my Brother MFC-7360N (network).

You might want to check out this link... [https://askubuntu.com/questions/652769/running-canon-120-lide-scanner-on-ubuntu-14-04]("https://askubuntu.com/questions/652769/running-canon-120-lide-scanner-on-ubuntu-14-04")
... for information relating to Canon 120 LiDE scanner.

You need correct driver and correct configuration.

---

### Post by eezacque on 2018-09-15
> **him610 said:**
> Well, that shows your scanner is recognized by your system, and I would think it is not hardware.

That is clear from the above post, where I write I often get bad scans.
If the scanner isn't recognised, you cannot scan at all.

---

### Post by eezacque on 2018-09-21
Anyone got this scanner working under Ubuntu 18.04.1?

---

### Post by eezacque on 2018-09-27
I returned this scanner to the supplier, who tested it and maintains there is nothing wrong with it.
As I have yet to find someone who runs this scanner under Ubuntu 18.04.1, I will assume it is not compatible.
Will file a bug report with SANE.

---

